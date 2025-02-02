##### Physics (PhysX)

# Composite objects (objects with affordances)

**Composite objects** are objects in TDW that have multiple "sub-objects". Sub-objects are differences from [sub-*meshes*](../objects_and_scenes/materials_textures_colors.md) in that they appear in [output data](../core_concepts/output_data.md) as separate objects with separate IDs and [segmentation colors](../visual_perception/id.md).

Composite objects can be:

- Objects with hinged joints such as a fridge with doors
- Objects with hinged motorized joints such as a fan
- Multiple disconnected objects such as a pot with a lid 
- An object with a light source such as a lamp

## Composite objects in the model library

Usually, composite objects in the [model library](../core_concepts/objects.md) have a `_composite` suffix in their names. However, a more reliable way to find composite objects is to test the `composite_object` boolean value:

```python
from tdw.librarian import ModelLibrarian

lib = ModelLibrarian()
for record in lib.records:
    if record.composite_object and not record.do_not_use:
        print(record.name)
```

## Manipulating composite objects

Sub-objects will respond to TDW commands just like any other object; you can, for example, [apply forces](forces.md) to individual sub-objects. Sub-objects likewise appear as separate objects in the output data.

Some sub-objects have additional functionality and specialized commands. To determine what they are, you must first send [`send_composite_objects`](../../api/command_api.md#send_composite_objects) which returns [`CompositeObjects`](../../api/output_data.md#CompositeObjects) output data:

```python
from tdw.controller import Controller
from tdw.tdw_utils import TDWUtils
from tdw.output_data import OutputData,CompositeObjects

c = Controller()
object_id = c.get_unique_id()
resp = c.communicate([TDWUtils.create_empty_room(12, 12),
                      c.get_add_object(model_name="puzzle_box_composite",
                                       object_id=object_id),
                      {"$type": "send_composite_objects"}])
for i in range(len(resp) - 1):
    r_id = OutputData.get_data_type_id(resp[i])
    if r_id == "comp":
        composite_objects = CompositeObjects(resp[i])
        # Iterate through each composite object.
        for j in range(composite_objects.get_num()):
            # Get the target composite object.
            if composite_objects.get_object_id(j) == object_id:
                # Iterate through each sub-object.
                for k in range(composite_objects.get_num_sub_objects(j)):
                    sub_object_id = composite_objects.get_sub_object_id(j, k)
                    sub_object_machine_type = composite_objects.get_sub_object_machine_type(j, k)
                    print(sub_object_id, sub_object_machine_type)
    c.communicate({"$type": "terminate"})
```

The "sub-object machine type" determines which API command can be used for this sub-object:

| Machine type | Behavior                                                     | Example                | Command                                                      |
| ------------ | ------------------------------------------------------------ | ---------------------- | ------------------------------------------------------------ |
| `"light"`    | Can be turned on and off.                                    | A lightbulb            | [`set_sub_object_light`](../../api/command_api.md#set_sub_object_light) |
| `"motor"`    | Can rotate on a pivot point around an axis by applying a target velocity and a force magnitude. | A helicopter propeller | [`set_motor`](../../api/command_api.md#set_motor)            |
| `"hinge"`    | Swings freely on a pivot point around an axis.               | A box with a lid       |                                                              |
| `"spring"`   | Can rotate on a pivot point around an axis by applying a target position. The motion will appear "spring-like". | Jack-in-the-box        | [`set_spring`](../../api/command_api.md#set_spring)          |
| `"none"`     | (no mechanism)                                               | A chest of drawers     |                                                              |

***

**Next: [Skip physics frames](step_physics.md)**

[Return to the README](../../../README.md)

***

Example controllers:

- [composite_object.py](https://github.com/threedworld-mit/tdw/blob/master/Python/example_controllers/physx/composite_object.py) Demonstration of how to use composite sub-objects with a test model.

Python API:

- [`ModelRecord.composite_object`](../../python/librarian/model_librarian.md) True if the record is for a composite object.

Command API:

- [`set_sub_object_light`](../../api/command_api.md#set_sub_object_light)
- [`set_motor`](../../api/command_api.md#set_motor)
- [`set_spring`](../../api/command_api.md#set_spring) 
- [`send_composite_objects`](../../api/command_api.md#send_composite_objects)

Output Data:

- [`CompositeObjects`](../../api/output_data.md#CompositeObjects) 