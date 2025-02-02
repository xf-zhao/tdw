# ThirdPersonCameraBase

`from tdw.add_ons.third_person_camera_base import ThirdPersonCameraBase`

An abstract base class for third-person camera controller add-ons.

***

## Fields

- `avatar_id` The ID of the avatar that (this camera).

- `position` The position of the camera. If None, defaults to `{"x": 0, "y": 0, "z": 0}`.

***

## Functions

#### \_\_init\_\_

**`ThirdPersonCameraBase()`**

**`ThirdPersonCameraBase(avatar_id=None, position=None, rotation=None, field_of_view=None)`**

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| avatar_id |  str  | None | The ID of the avatar (camera). If None, a random ID is generated. |
| position |  Dict[str, float] | None | The initial position of the camera. If None, defaults to `{"x": 0, "y": 0, "z": 0}`. |
| rotation |  Dict[str, float] | None | The initial rotation of the camera. Can be Euler angles (keys are `(x, y, z)`) or a quaternion (keys are `(x, y, z, w)`). If None, defaults to `{"x": 0, "y": 0, "z": 0}`. |
| field_of_view |  int  | None | If not None, set the field of view. |

#### on_send

_(Abstract)_

**`self.on_send(resp)`**

This is called after commands are sent to the build and a response is received.

Use this function to send commands to the build on the next frame, given the `resp` response.
Any commands in the `self.commands` list will be sent on the next frame.

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| resp |  List[bytes] |  | The response from the build. |

#### get_initialization_commands

**`self.get_initialization_commands()`**

This function gets called exactly once per add-on. To re-initialize, set `self.initialized = False`.

_Returns:_  A list of commands that will initialize this add-on.

#### before_send

**`self.before_send(commands)`**

This is called before sending commands to the build. By default, this function doesn't do anything.

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| commands |  List[dict] |  | The commands that are about to be sent to the build. |

