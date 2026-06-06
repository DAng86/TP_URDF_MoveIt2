# ROS 2 Robotic Arm – URDF/Xacro and MoveIt 2 Assignment

## Project Overview

This project demonstrates the modelling and visualisation of a robotic arm using ROS 2 Jazzy, URDF/Xacro, RViz and MoveIt 2.

The project includes:

- Creation of a ROS 2 robot description package.
- Development of a clean robotic arm model using Xacro.
- Definition of links, joints, collision geometry and inertial properties.
- Visualisation of the robot in RViz.
- Joint movement testing using Joint State Publisher GUI.
- Generation of a MoveIt 2 configuration package using MoveIt Setup Assistant.
- Creation of a planning group and self-collision matrix.

## Workspace Structure

ri_ws/
src/
robot_arm_clean_description/
urdf/
clean_robot_arm.urdf.xacro
launch/
display.launch.py
rviz/
clean_robot_arm.rviz
screenshots/
robot_arm_clean_moveit_config/

## Robot Description

The clean robotic arm consists of the following links:

- world
- base_link
- shoulder_link
- upper_arm_link
- forearm_link
- wrist_link
- gripper_link
- left_finger_link
- right_finger_link

The main revolute joints are:

- joint1
- joint2
- joint3
- joint4
- joint5

The gripper fingers are connected using fixed joints.

## Running the RViz Model

Build the workspace:

cd ~/ri_ws
colcon build
source install/setup.bash

Launch the clean robot model:

LIBGL_ALWAYS_SOFTWARE=1 ros2 launch robot_arm_clean_description display.launch.py

This opens RViz, Robot State Publisher and Joint State Publisher GUI.

The robot can be moved using the joint sliders.

## MoveIt 2 Configuration

A separate MoveIt 2 package was generated:

robot_arm_clean_moveit_config

MoveIt Setup Assistant was used to configure:

- Self-collision matrix
- Planning group: arm
- Joints included in the planning group:
  - joint1
  - joint2
  - joint3
  - joint4
  - joint5
- ROS 2 controller: arm_controller

## Screenshots

The screenshots folder contains evidence of:

- Initial robot model in RViz.
- RobotModel status OK.
- Visual and collision geometry enabled.
- Joint movement for joint1 to joint5.
- MoveIt Setup Assistant collision matrix.
- MoveIt package generation.

## Known Issue

The robot model and joint movement work correctly in RViz. The MoveIt 2 configuration package was generated successfully. However, during final MoveIt demo launch, the OMPL planning plugin produced a planning pipeline loading error:

Planning plugin name is empty or not defined in namespace 'ompl'

Due to time constraints, this issue was documented as a known limitation. The URDF/Xacro model, RViz visualisation, joint movement and MoveIt Setup Assistant configuration were completed and verified.

## Conclusion

The assignment demonstrates the creation of a clear robotic arm model using ROS 2, URDF/Xacro and RViz. The robot model is functional, visually clear, and all five revolute joints can be moved through Joint State Publisher GUI. A MoveIt 2 configuration package was also generated for the robot arm.
