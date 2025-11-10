# ugv_ddsm #
![OS](https://img.shields.io/ubuntu/v/ubuntu-wallpapers/noble)
![ROS_2](https://img.shields.io/ros/v/jazzy/rclcpp)

use command to review the urdf model:
ros2 launch urdf_tutorial display.launch.py model:=/workspaces/isaac_ros-dev/src/ugv_ddsm/ugv_ddsm_description/urdf/robots/Robot_wrapper.urdf.xacro

ros2 launch ugv_ddsm_description robot_state_publisher.launch.py

bash /workspaces/isaac_ros-dev/src/ugv_ddsm/ugv_ddsm_bringup/scripts/ugv_ddsm_gazebo.sh