# Robot

`from tdw.add_ons.robot import Robot`

Add a robot to the scene and set joint targets and add joint forces. It has static and dynamic (per-frame) data for each of its joints.

```python
from tdw.controller import Controller
from tdw.tdw_utils import TDWUtils
from tdw.add_ons.robot import Robot

c = Controller()
# Add a robot.
robot = Robot(name="ur5",
              position={"x": -1, "y": 0, "z": 0.5},
              robot_id=0)
c.add_ons.append(robot)
# Initialize the scene.
c.communicate([{"$type": "load_scene",
                "scene_name": "ProcGenScene"},
               TDWUtils.create_empty_room(12, 12)])
# Set joint targets.
robot.set_joint_targets({robot.static.joint_ids_by_name["shoulder_link"]: 15,
                         robot.static.joint_ids_by_name["upper_arm_link"]: -45,
                         robot.static.joint_ids_by_name["forearm_link"]: 60})
# Wait until the robot stops moving.
while robot.joints_are_moving():
    c.communicate([])
c.communicate({"$type": "terminate"})
```

***

## Fields

- `static` [Static robot data.](../robot_data/robot_static.md)

- `dynamic` [Dynamic robot data.](../robot_data/robot_dynamic.md)

- `name` The name of the robot.

- `url` The URL or filepath of the robot asset bundle.

***

## Functions

#### \_\_init\_\_

**`Robot(name)`**

**`Robot(name, robot_id=0, position=None, rotation=None, source=None)`**

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| name |  str |  | The name of the robot. |
| robot_id |  int  | 0 | The ID of the robot. |
| position |  Dict[str, float] | None | The position of the robot. If None, defaults to `{"x": 0, "y": 0, "z": 0}`. |
| rotation |  Dict[str, float] | None | The rotation of the robot in Euler angles (degrees). If None, defaults to `{"x": 0, "y": 0, "z": 0}`. |
| source |  Union[RobotLibrarian, RobotRecord, str] | None | The source file of the robot. If None: The source will be the URL of the robot record in TDW's built-in [`RobotLibrarian`](../librarian/robot_librarian.md). If `str`: This is a filepath (starts with `file:///`) or a URL (starts with `http://` or `https://`). If `RobotRecord`: the source is the URL in the record. If `RobotLibrarian`: The source is the record in the provided `RobotLibrarian` that matches `name`. |

#### set_joint_targets

**`self.set_joint_targets(targets)`**

Set target angles or positions for a dictionary of joints.

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| targets |  Dict[int, Union[float, Dict[str, float] |  | A dictionary of joint targets. Key = The ID of the joint. Value = the targets. For spherical joints, this must be a Vector3 dictionary, for example `{"x": 40, "y": 0, "z": 0}` (angles in degrees). For revolute joints, this must be a float (an angle in degrees). For prismatic joints, this must be a float (a distance in meters). |

#### add_joint_forces

**`self.add_joint_forces(forces)`**

Add torques and forces to a dictionary of joints.

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| forces |  Dict[int, Union[float, Dict[str, float] |  | A dictionary of joint forces. Key = The ID of the joint. Value = the targets. For spherical joints, this must be a Vector3 dictionary, for example `{"x": 40, "y": 0, "z": 0}` (torques in Newtons). For revolute joints, this must be a float (a torque in Newtons). For prismatic joints, this must be a float (a force in Newtons). |

#### stop_joints

**`self.stop_joints()`**

**`self.stop_joints(joint_ids=None)`**

Stop the joints at their current angles or positions.

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| joint_ids |  List[int] | None | A list of joint IDs. If None, stop all joints. |

