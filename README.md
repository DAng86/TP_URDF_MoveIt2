# ROS 2 Robotic Arm – URDF/Xacro and MoveIt 2 Assignment

## 1. Project Overview

This project was carried out for the Industrial Robotics assignment on robotic arm modelling using ROS 2, URDF/Xacro, RViz 2 and MoveIt 2.

The objective was to create a complete robot description, visualise the robot in RViz 2, verify joint movements, generate a MoveIt 2 configuration package, and demonstrate motion planning in simulation.

The implementation was done using:

- Ubuntu 24.04
- ROS 2 Jazzy
- RViz 2
- MoveIt 2
- URDF/Xacro

The final implementation uses two main ROS 2 packages:

- `robot_arm_clean_description`
- `robot_arm_clean_moveit_config`

## 2. Choice and Justification of URDF/Xacro Representation

A Xacro-based architecture was selected for the robot description.

This choice was made because Xacro improves readability, modularity and maintainability compared with a single large URDF file. The robotic arm contains several links, joints, visual origins, collision elements and inertial properties. Using Xacro makes it easier to organise the robot model and modify parameters.

## 3. Robot Description

The robot arm was modelled with multiple links and joints. The description includes:

- visual elements;
- collision geometries;
- inertial properties;
- joint origins;
- joint axes;
- joint limits.

The main robot description files are located in:

```bash
src/robot_arm_clean_description/urdf/
