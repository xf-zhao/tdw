# ThreeDWorld (TDW)

**ThreeDWorld (TDW)** is a platform for interactive multi-modal physical simulation. With TDW, users can simulate high-fidelity sensory data and physical interactions between mobile agents and objects in a wide variety of rich 3D environments.

TDW is a general-purpose tool that allows the user to communicate and manipulate a 3D environment. As such, there's no single "correct" procedure for using TDW. This guide will show you how to start using TDW and how to explore the available options.

- [Code of Conduct](https://github.com/threedworld-mit/tdw/blob/master/code_of_conduct.md)
- [Changelog](https://github.com/threedworld-mit/tdw/blob/master/Documentation/Changelog.md)
- [License](https://github.com/threedworld-mit/tdw/blob/master/LICENSE.txt)
- [Website](http://threedworld.org/)

# 1. General guide to TDW

## 1.1 Setup

1. [Install TDW](Documentation/lessons/setup/install.md)
2. [Auto-launching the TDW build](Documentation/lessons/setup/launch_build.md)
3. [Upgrade TDW](Documentation/lessons/setup/upgrade.md)

## 1.2 Core Concepts

1. [The controller](Documentation/lessons/core_concepts/controller.md)
2. [Commands](Documentation/lessons/core_concepts/commands.md)
3. [Design philosophy of TDW](Documentation/lessons/core_concepts/design_philosophy.md)
4. [Scenes](Documentation/lessons/core_concepts/scenes.md)
5. [Avatars and cameras](Documentation/lessons/core_concepts/avatars.md)
6. [Objects](Documentation/lessons/core_concepts/objects.md)
7. [Output data](Documentation/lessons/core_concepts/output_data.md)
8. [Images](Documentation/lessons/core_concepts/images.md)

## 1.3 Troubleshooting and good coding practices :warning: TODO :warning:

- [ ] Common errors
- [ ] Debug logging
- [ ] Good coding practices
- [ ] Performance optimizations
- [ ] Performance benchmarks

# 2. Tutorials :warning: TODO :warning:

## 2.1 Objects and Scenes

1. Overview
2. [Units and data formats](Documentation/lessons/objects_and_scenes/units.md)
3. `Bounds` output data
4. Rotating objects
5. Kinematic objects
6. Put one object on top of another
7. Reset a scene
8. Procedural generation

## 2.2 Non-Default 3D Models

- [ ] Overview
- [ ] Free models
- [ ] Non-free models
- [ ] Add your own models to TDW
- [ ] Add ShapeNet models to TDW
- [ ] FloorplanController (high-level API)

## 2.3 Visual perception

1. [Overview](Documentation/lessons/visual_perception/overview.md)
2. [Segmentation colors (`_id` pass)](Documentation/lessons/visual_perception/id.md)
3. [Segmentation colors (`_category` pass)](Documentation/lessons/visual_perception/category.md)
4. [Depth maps (`_depth` and `_depth_simple` passes)](Documentation/lessons/visual_perception/depth.md)
5. [Motion perception (`_flow` pass)](Documentation/lessons/visual_perception/flow.md)
6. [Other image passes (`_mask`, `_normals`, and `_albedo` passes)](Documentation/lessons/visual_perception/other_passes.md)
7. [`Occlusion` output data](Documentation/lessons/visual_perception/occlusion.md)
8. Camera rotation

## 2.4 Photorealistic images

- [ ] Visual materials, textures, and colors
- [ ] Lighting
- [ ] Post-processing
- [ ] Depth of field
- [ ] Anti-aliasing
- [ ] Image-only videos

High-level API: [tdw_image_dataset](https://github.com/alters-mit/tdw_image_dataset)

## 2.5 Physics

- [ ] Overview
- [ ] Collisions
- [ ] Friction
- [ ] Default object physics parameters
- [ ] NVIDIA Flex
- [ ] tdw_physics (high-level API)

## 2.6 Audio

- [ ] Overview
- [ ] Resonance Audio
- [ ] PyImpact
- [ ] Recording audio
- [ ] Recording audio+video
- [ ] Audio perception
- [ ] multimodal_challenge (use case)

## 2.7 Robots and embodied agents

- [ ] Robots
- [ ] Composite objects
- [ ] VR
- [ ] Humanoids
- [ ] Keyboard controls
- [ ] NavMesh
- [ ] magnebot (high-level API)

## 2.8 Misc. topics

- [ ] C# source code
- [ ] Freezing your code
- [ ] BinaryManager
- [ ] xpra

# 3. API Documentation

TODO

## :warning: old documentation :warning:

### [C# Code](https://github.com/threedworld-mit/tdw/blob/master/Documentation/contributions/c_sharp_sources.md)

# API

#### Commands and Output Data

| Document                                                    | Description                                                  |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| [Command API](https://github.com/threedworld-mit/tdw/blob/master/Documentation/api/command_api.md)             | API for every command a controller can send to the build.    |
| [Command API Guide](https://github.com/threedworld-mit/tdw/blob/master/Documentation/api/command_api_guide.md) | Overview of how to send commands to the build.               |
| [Output Data](https://github.com/threedworld-mit/tdw/blob/master/Documentation/api/output_data.md)             | API for all output data a controller can receive from the build. |

#### High-Level APIs

| API                                                          | Description                                    |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [Image dataset](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/use_cases/single_object.md) | Generate 1.3M photorealistic images.           |
| [tdw_physics](https://github.com/alters-mit/tdw_physics)     | Generate physics datasets.                     |
| [Magnebot](https://github.com/alters-mit/magnebot)           | High-level Magnebot robotics API.              |
| [Transport Challenge](https://github.com/alters-mit/transport_challenge) | A higher-level API that uses the Magnebot API. |

#### Python `tdw` module

##### Frontend

| Document                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [`tdw` module](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/tdw.md) | Overview of the Python `tdw` module.                         |
| [Controller](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/controller.md) | Base class for all controllers.                              |
| [TDWUtils](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/tdw_utils.md) | Utility class.                                               |
| [AssetBundleCreator](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/asset_bundle_creator.md) | Covert 3D models into TDW-compatible asset bundles.          |
| [PyImpact](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/py_impact.md) | Generate impact sounds at runtime.                           |
| [FloorplanController](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/floorplan_controller.md) | Child class of `Controller` that creates an interior environment and populates it with objects. |
| [Librarian](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/librarian/librarian.md) | "Librarians" hold asset bundle metadata records.             |
| [FluidTypes](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/fluid_types.md) | Access different NVIDIA Flex fluid types.                    |
| [Object Init Data](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/object_init_data.md) | Wrapper classes for storing object initialization data.      |
| [AddOn](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/add_on.md) | Overview of how add-ons work and API documentation for the abstract `AddOn` class. |
| [Benchmark](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/benchmark.md) | An add-on that can be used to benchmark your controller.     |
| [CinematicCamera](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/cinematic_camera.md) | An add-on that adds a "cinematic" camera to the scene.       |
| [Debug](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/cinematic_camera.md) | An add-on that can help debug your controller.               |
| [ImageCapture](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/cinematic_camera.md) | An add-on that will save images to disk per-frame.           |
| [Keyboard](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/cinematic_camera.md) | An add-on that adds keyboard controls.                       |
| [OccupancyMap](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/occupancy_map.md) | Generated navigation occupancy maps for a scene.             |
| [ThirdPersonCamera](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/cinematic_camera.md) | An add-on that adds a third-person camera to the scene.      |

##### Backend

| Document                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Build](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/build.md) | Helper functions for downloading the build.                  |
| [PyPi](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/pypi.md) | Helper functions for checking the version of the `tdw` module on PyPi. |

# Audio and Video

| Document                                                     | Description                                       |
| ------------------------------------------------------------ | ------------------------------------------------- |
| [Impact Sounds](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/impact_sounds.md) | Generate impact sounds at runtime using PyImpact. |
| [PyImpact](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/py_impact.md)                | PyImpact API.                                     |
| [Audio/Video Recording](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/video.md) | Record audio, video, or audio+video.              |
| [Remote rendering](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/xpra.md)      | How to render using xpra.                         |
| [CinematicCamera](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/cinematic_camera.md) | An add-on that adds a "cinematic" camera to the scene. |
| [ImageCapture](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/cinematic_camera.md) | An add-on that will save images to disk per-frame. |
| [ThirdPersonCamera](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/cinematic_camera.md) | An add-on that adds a third-person camera to the scene. |

# Avatars (Agents)

| Document                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Observation Data](https://github.com/threedworld-mit/tdw/blob/master/Documentation/benchmark/observation_data.md) | Different means of determining what an agent is observing.   |
| [Depth Maps](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/depth.md) | How to use depth maps.                                       |
| [Avatar Movement](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/avatar_movement.md) | Different techniques for moving agents.                      |
| [Magnebot](https://github.com/alters-mit/magnebot)           | High-level Magnebot API.                      |
| [CinematicCamera](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/cinematic_camera.md) | An add-on that adds a "cinematic" camera to the scene. |
| [ImageCapture](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/cinematic_camera.md) | An add-on that will save images to disk per-frame. |
| [ThirdPersonCamera](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/cinematic_camera.md) | An add-on that adds a third-person camera to the scene. |

# Benchmarks and Speed

| Document                                                     | Description                |
| ------------------------------------------------------------ | -------------------------- |
| [Benchmark](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/benchmark.md) | An add-on that can be used to benchmark your controller. |
| [Benchmarks](https://github.com/threedworld-mit/tdw/blob/master/Documentation/benchmark/benchmark.md)           | Performance benchmarks.    |
| [Performance Optimizations](https://github.com/threedworld-mit/tdw/blob/master/Documentation/benchmark/performance_optimizations.md) | Increase simulation speed. |

# Examples

| Document                                                     | Description                                                |
| ------------------------------------------------------------ | ---------------------------------------------------------- |
| [Example Controllers](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/example_controllers.md) | Index of all example controllers in the repo.              |
| Use Cases (see below)                                        | The "use cases" section showcases "advanced" usage of TDW. |

# Misc.

| Document                                                     | Description                          |
| ------------------------------------------------------------ | ------------------------------------ |
| [VR](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/vr.md) | VR in TDW.                           |
| [Humanoids](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/humanoids.md) | Add "humanoids" and play animations. |

# Physics (PhysX and Flex)

| Document                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Physics](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/physics.md) | Common physics problems and solutions.                       |
| [NVIDIA Flex](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/flex.md) | Add soft bodies, cloth, and fluids to TDW.                   |
| [FluidTypes](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/fluid_types.md) | Access different NVIDIA Flex fluid types.                    |
| [Physics Determinism](https://github.com/threedworld-mit/tdw/blob/master/Documentation/benchmark/determinism.md) | Benchmark of PhysX physics determinism.                      |
| [tdw_physics](https://github.com/alters-mit/tdw_physics)     | Generate a physics dataset.                                  |
| [Rube Goldberg (demo)](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/use_cases/rube_goldberg.md) | Demo of complex physical interactions between objects, with PyImpact generation of impact sounds, set in a photorealistic scene. |

# Releases

| Document | Description |
| --- | --- |
| [C# code](https://github.com/threedworld-mit/tdw/blob/master/Documentation/contributions/c_sharp_sources.md) | Access to C# backend source code |
| [Releases](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/releases.md) | Release versioning in TDW.           |
| [Freezing your code](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/freeze.md) | "Freeze" your controller into a compiled executable. |

# Remote Server

| Document                                                | Description                                                 |
| ------------------------------------------------------- | ----------------------------------------------------------- |
| [Docker](https://github.com/threedworld-mit/tdw/blob/master/Documentation/Docker/docker.md)                | Create a Docker container for TDW.                          |
| [Remote rendering](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/xpra.md) | How to render using xpra.                                   |
| [BinaryManager](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/binary_manager.md) | Manage multiple instances of TDW builds on a remote server. |
| [bash scripts](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/bash.md)     | Useful bash scripts for Linux.                              |

# Rendering and Photorealism

| Document                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Asset Bundle Librarians](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/librarian/librarian.md) | Overview of what asset bundles are, how to add objects, scenes, materials, HDRI skyboxes, and humanoids, and how to access each asset bundle's metadata. |
| [Model Screenshotter](https://github.com/threedworld-mit/tdw/blob/master/Documentation/utility_applications/model_screenshotter.md) | Generate images of every model in TDW.                       |
| [Material Screenshotter](https://github.com/threedworld-mit/tdw/blob/master/Documentation/utility_applications/material_screenshotter.md) | Generate images of every material in TDW.                    |
| [Materials, textures, and colors](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/materials_textures_colors.md) | Defines materials, textures, and colors.                     |
| [Depth of Field](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/depth_of_field_and_image_blurriness.md) | Prevent blurry images and increase realism.                  |
| [Depth Maps](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/depth.md) | How to use depth maps.                                       |
| [Remote rendering](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/xpra.md) | How to render using xpra.                                    |
| [Observation Data](https://github.com/threedworld-mit/tdw/blob/master/Documentation/benchmark/observation_data.md) | Different means of determining what an agent is observing.   |
| [CinematicCamera](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/cinematic_camera.md) | An add-on that adds a "cinematic" camera to the scene. |
| [ImageCapture](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/cinematic_camera.md) | An add-on that will save images to disk per-frame. |
| [ThirdPersonCamera](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/cinematic_camera.md) | An add-on that adds a third-person camera to the scene. |

# Robotics

| Document                                                     | Description                                   |
| ------------------------------------------------------------ | --------------------------------------------- |
| [Robots](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/robots.md) | Overview of robotics and the Magnebot in TDW. |
| [Robot Librarian](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/librarian/robot_librarian.md) | API for accessing robot metadata.             |
| [Robot Creator](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/robot_creator.md) | API for adding your own robots to TDW.        |
| [Magnebot](https://github.com/alters-mit/magnebot)           | High-level Magnebot API.                      |

# Scene Setup

| Document                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Scene Setup](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/scene_setup.md) | Overview of how to set up a scene.                           |
| [Asset Bundle Librarians](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/librarian/librarian.md) | Overview of what asset bundles are, how to add objects, scenes, materials, HDRI skyboxes, and humanoids, and how to access each asset bundle's metadata. |
| [Model Librarian](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/librarian/model_librarian.md) | Overview of how to add objects and access metadata.          |
| [Rotation](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/rotation.md) | Different means of rotating objects and agents in a scene.   |
| [Scene Reset](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/reset_scene.md) | How to reset a scene.                                        |
| [FloorplanController](Documentation/python/floorplan_controller.md) | Child class of `Controller` that creates an interior environment and populates it with objects. |

# TDW and 3D Objects

| Document                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Model Librarian](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/librarian/model_librarian.md) | Overview of how to add objects and access metadata.          |
| [Model Screenshotter](https://github.com/threedworld-mit/tdw/blob/master/Documentation/utility_applications/model_screenshotter.md) | Generate images of every model in TDW.                       |
| [Non-free models](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/models_full.md) | Access the TDW "full model library".                         |
| [Local 3D models](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/add_local_object.md) | Add your own objects to TDW.                                 |
| [ShapeNet models](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/shapenet.md) | Convert ShapeNET models into TDW objects.                    |
| [Composite Objects](Documentation/composite_objects/composite_objects.md)<br>[Creating Composite Objects](https://github.com/threedworld-mit/tdw/blob/master/Documentation/composite_objects/creating_composite_objects.md) | Use and create "composite objects".                          |
| [AssetBundleCreator](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/asset_bundle_creator.md) | API for the `AssetBundleCreator` class (used to convert 3D models into TDW-compatible asset bundles). |
| [Rotation](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/rotation.md) | Different means of rotating objects and agents in a scene.   |
| [AddOn](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/add_ons/add_on.md) | Overview of how add-ons work and API documentation for the abstract `AddOn` class. |

# Troubleshooting TDW

| Document                                                     | Description                                           |
| ------------------------------------------------------------ | ----------------------------------------------------- |
| [Debug TDW](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/debug_tdw.md) | Several strategies for debugging errors in your code. |
| [Depth of Field](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/depth_of_field_and_image_blurriness.md) | Prevent blurry images and increase realism.           |
| [Performance Optimizations](https://github.com/threedworld-mit/tdw/blob/master/Documentation/benchmark/performance_optimizations.md) | Increase simulation speed.                            |
| [OS X](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/osx.md) | Common OS X problems and solutions.                   |
| [Physics](https://github.com/threedworld-mit/tdw/blob/master/Documentation/misc_frontend/physics.md) | Common physics problems and solutions.                |

# Use Cases

| Use Case                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Image dataset](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/use_cases/single_object.md) | Generate 1.3M photorealistic images.                         |
| [IntPhys (demo)](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/use_cases/int_phys.md) | Demo of how to simulate IntPhys in TDW.                      |
| [Humanoid videos](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/use_cases/humanoid_video.md) | Generate a dataset of humanoid animations.                   |
| [tdw_physics](https://github.com/alters-mit/tdw_physics)     | Generate a physics dataset.                                  |
| [Rube Goldberg (demo)](https://github.com/threedworld-mit/tdw/blob/master/Documentation/python/use_cases/rube_goldberg.md) | Demo of complex physical interactions between objects, with PyImpact generation of impact sounds, set in a photorealistic scene. |
| [Magnebot](https://github.com/alters-mit/magnebot)           | High-level Magnebot API.                                     |