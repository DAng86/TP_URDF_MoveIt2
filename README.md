# ROS 2 Robotic Arm – URDF/Xacro and MoveIt 2 Assignment

## 1. Project Overview

This project was carried out for the modelling of a robotic arm using ROS 2, URDF/Xacro, RViz 2 and MoveIt 2.

The objective of the assignment was to create a complete robot description, visualise the robot in RViz 2, verify the joint movements, generate a MoveIt 2 configuration package, and demonstrate trajectory planning in simulation.

The implementation was done using:

- Ubuntu 24.04
- ROS 2 Jazzy
- RViz 2
- MoveIt 2
- URDF/Xacro

The final implementation contains two main ROS 2 packages:

- robot_arm_clean_description
- robot_arm_clean_moveit_config

## 2. URDF/Xacro Representation

A Xacro-based architecture was selected for the robot description.
The robotic arm contains several links, joints, visual origins, collision elements and inertial properties. Using Xacro makes it easier to organise the robot model and modify parameters if required.

## 3. Robot Description

The robotic arm was modelled with multiple links and joints. The description includes:

- visual elements;
- collision geometries;
- inertial properties;
- joint origins;
- joint axes;
- joint limits.

The main robot description files are located in:

src/robot_arm_clean_description/urdf/

Important files:

- clean_robot_arm.urdf.xacro
- clean_robot_arm.urdf

The main revolute joints used for the robotic arm are:

- joint1
- joint2
- joint3
- joint4
- joint5

The robot can be visualised in RViz using the display launch file included in the description package.

## 4. Assumptions on Masses, Inertias and Joint Limits

Approximate values have been used for the inertial properties. The masses and inertia tensors were estimated to allow the URDF/Xacro model to remain valid and usable in ROS 2 tools.

The following assumptions were made:

- Each link was assigned a reasonable estimated mass suitable for a small educational robotic arm.
- The inertia tensors were approximated to keep the model valid for ROS 2 tools.
- Revolute joints were assigned coherent lower and upper angular limits.
- Velocity limits were defined for each joint.
- Acceleration limits were enabled in joint_limits.yaml so that MoveIt 2 could generate valid trajectories.

The joint limits were selected to provide coherent and safe motion for a small robotic arm. Revolute joints were limited using reasonable lower and upper angular bounds. Velocity and acceleration limits were also defined so that MoveIt 2 could generate valid trajectories.

## 5. RViz 2 Visualisation

The robot model was launched and checked in RViz 2. The following points were verified:

- the robot model loads correctly;
- the RobotModel status is OK;
- the joints can be moved using the Joint State Publisher GUI;
- each articulation produces visible movement;
- the visual and collision representations are available.

Launch command:

cd ~/ri_ws
source install/setup.bash
ros2 launch robot_arm_clean_description display.launch.py

LIBGL_ALWAYS_SOFTWARE=1 ros2 launch robot_arm_clean_description display.launch.py

Screenshots of the robot model and joint movements are included in:

src/robot_arm_clean_description/screenshots/

## 6. MoveIt 2 Configuration

The MoveIt 2 configuration package was generated using the MoveIt Setup Assistant.

The generated package is:

robot_arm_clean_moveit_config

The MoveIt 2 configuration includes:

- SRDF file;
- self-collision matrix;
- planning group named arm;
- kinematics configuration;
- joint limits;
- OMPL planning configuration;
- RViz configuration for MoveIt 2;
- launch files for the MoveIt 2 demo.

Important files are located in:

src/robot_arm_clean_moveit_config/config/
src/robot_arm_clean_moveit_config/launch/

The planning group used for the robot arm is:

arm

The joints included in the planning group are:

- joint1
- joint2
- joint3
- joint4
- joint5

## 7. MoveIt 2 Motion Planning Demonstration

MoveIt 2 was launched using:

cd ~/ri_ws
source install/setup.bash
ros2 launch robot_arm_clean_moveit_config demo.launch.py

In RViz 2, the planning group arm was selected. A random valid goal state was generated and a valid motion plan was computed and visualised.

This demonstrates that the robot arm was successfully integrated into the MoveIt 2 planning pipeline.

## 8. Build Instructions

To build the workspace:

cd ~/ri_ws
colcon build
source install/setup.bash

## 9. Package Structure

The workspace contains the following main packages:

ri_ws/
- README.md
- src/
  - robot_arm_clean_description/
    - CMakeLists.txt
    - package.xml
    - launch/
    - rviz/
    - screenshots/
    - urdf/
  - robot_arm_clean_moveit_config/
    - CMakeLists.txt
    - package.xml
    - config/
    - launch/

The robot_arm_clean_description package contains the robot model, RViz configuration, launch files and screenshots.

The robot_arm_clean_moveit_config package contains the MoveIt 2 configuration generated using the MoveIt Setup Assistant.

## 10. Screenshots

The submitted screenshots demonstrate:

- robot model loaded in RViz 2;
- RobotModel status OK;
- individual joint movements;
- collision representation;
- MoveIt Setup Assistant collision matrix generation;
- MoveIt package generation;
- MoveIt 2 planning demonstration;
- robot arm in a planned pose.

Screenshots are stored in:

src/robot_arm_clean_description/screenshots/

## 11. Difficulties Encountered and Solutions

### Difficulty 1: RViz and Virtual Machine Performance

RViz 2 and MoveIt 2 required sufficient graphical resources in the Ubuntu virtual machine. The VM settings and rendering options were adjusted to improve stability and allow RViz 2 to run correctly.

### Difficulty 2: MoveIt 2 Trajectory Planning Error

During testing, MoveIt 2 initially failed to generate a trajectory because the acceleration limits were not properly enabled in the joint_limits.yaml file.

This was corrected by enabling acceleration limits and defining suitable acceleration values for the joints.

### Difficulty 3: Validation of the MoveIt 2 Pipeline

The MoveIt 2 planning interface was tested using a random valid goal state. After correcting the joint limits, the robot arm successfully generated and visualised a motion plan in RViz 2.

## 12. Conclusion

The robotic arm was successfully modelled using URDF/Xacro, visualised in RViz 2, and configured with MoveIt 2. The final system demonstrates a complete workflow from robot description to motion planning simulation.

