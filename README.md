# UGV-DDSM

## Overview

UGV-DDSM is a ROS 2 package for the Universal Ground Vehicle - Differential Drive Scout Mobile robot. This package provides all necessary configuration files, URDF models, controllers, and launch files to simulate and control the robot in both Gazebo simulation and real-world scenarios.

The robot features a 4-wheel differential drive configuration with support for:
- Differential drive kinematics
- Joint state publishing
- Odometry estimation
- Gazebo simulation with realistic physics
- Real hardware control via ros2_control

## Prerequisites

- Ubuntu 22.04
- ROS 2 Humble
- Required ROS 2 packages:
  ```bash
  sudo apt install ros-humble-ros2-control ros-humble-ros2-controllers ros-humble-xacro ros-humble-teleop-twist-keyboard
  ```

## Setup

1. Clone this repository into your ROS 2 workspace:
   ```bash
   cd ~/study/ros/ugv_ddsm_ws/src
   git clone <repository_url>
   ```

2. Set up the Gazebo model path:
   ```bash
   export GZ_SIM_RESOURCE_PATH=../src/ugv_ddsm/ugv_ddsm_gazebo/models
   ```

3. Build the packages:
   ```bash
   cd ~/study/ros/ugv_ddsm_ws
   colcon build --symlink-install
   ```

4. Source the workspace:
   ```bash
   source install/setup.bash
   ```

## Packages

This repository contains the following packages:

- **ugv_ddsm**: Main metapackage
- **ugv_ddsm_bringup**: Launch files and configurations for bringing up the robot
- **ugv_ddsm_description**: URDF model and robot description files
- **ugv_ddsm_gazebo**: Gazebo simulation files and configurations
- **ugv_ddsm_system_tests**: System-level tests (currently empty)

## Usage

### Simulation

To launch the robot in Gazebo simulation:

```bash
ros2 launch ugv_ddsm_gazebo ugv_ddsm.gazebo.launch.py
```

### Visualization

To visualize the robot in RViz:

```bash
ros2 launch ugv_ddsm_description robot_state_publisher.launch.py
```

### Teleoperation

To teleoperate the robot with a joystick:

```bash
ros2 launch ugv_ddsm_bringup teleop.launch.py
```

### Navigation

To launch the navigation stack:

```bash
ros2 launch ugv_ddsm_bringup ugv_ddsm_navigation.launch.py
```

## Controllers

The robot uses the following controllers:
- **diff_drive_controller**: Controls the differential drive movement
- **joint_state_broadcaster**: Publishes joint states

These controllers can be loaded using:
```bash
ros2 control load_controller --set-state active diff_drive_controller --controller-manager /controller_manager
ros2 control load_controller --set-state active joint_state_broadcaster --controller-manager /controller_manager
```

Or through the provided launch file:
```bash
ros2 launch ugv_ddsm_bringup load_ros2_controllers.launch.py
```

## Configuration

Controller configurations are defined in:
- `ugv_ddsm_description/config/ugv_ddsm/ros2_controllers.yaml`

Robot parameters such as wheel separation and radius can be adjusted in this file.