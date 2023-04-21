# robotic_integration_hc10

This repository contains code and files related to the integration of the Yaskawa HC10 robot with ROS-based tools for trajectory planning and simulation. 

## Environment : Virtual Machine
To run the trajectory planning and simulation demonstrations, first ensure that ROS and the necessary ROS packages are installed.

Ubuntu 20.04  
Ros Noetic + packages moveIt, Ros control, ...  
Visual Studio Code  
Python 3  


## Getting Started
Getting started with the ROS Environment and MoveIt Trajectory Generation Tool.


```bash
cd robotic_integreation_hc10/catkin_ws
catkin build 
source devel/setup.bash 
```

### Demonstration in Rviz
This demonstration is more lightweight and suitable for testing motion planning algorithms and robot visualization. It contains a fake controller, which means that it does not take into account the physical laws. 

##### Step 1 :
Navigate to the catkin_ws directory within the robotic_integration_hc10:
```bash
cd robotic_integreation_hc10/catkin_ws
```
##### Step 2 :
Open a new terminal window and launch the MoveIt demo with the fake controller. The next command will start the MoveIt simulation environment with the HC10 robot in Rviz. 
 ```bash
roslaunch hc10_moveit_config demo_fake.launch 
```
##### Step 3 :
In a second terminal window, run the hc10\_move\_arm.py script to execute predefined motion commands for the HC10 robot:
```bash
rosrun hc10_moveit_config  hc10_move_arm.py
```

### Demonstration in Rviz and Gazebo

The second demonstration is more appropriate for testing and validating robot behavior in real-world scenarios. It includes the ros controller and Gazebo packages to create a more realistic simulation environment.Furthermore, it incorporates a pipeline sensor, namely the Kinect, which uses octomap to provide a more detailed and accurate mapping of the environment.


##### Step 1 :
Navigate to the catkin_ws directory within the robotic_integration_hc10:
```bash
cd robotic_integreation_hc10/catkin_ws
```

##### Step 2 :
Open a new terminal window and launch the MoveIt demo with the fake controller. The next command will start the MoveIt simulation environment with the HC10 robot in Rviz. 
 ```
roslaunch hc10_moveit_config demo_gazebo.launch 
```

##### Step 3 :
In a second terminal window, run the hc10_move_arm.py script to execute predefined motion commands for the HC10 robot:
```
rosrun hc10_moveit_config  hc10_move_arm_kinect.py 
```


## Trajectory planning visualisation on RViz
In this approach, trajectory planning is first visualized on RViz with a fake controller, it means that it does not take into account of physical laws. The trajectory is planned and executed between the initial and target poses previously configured in the MoveIt Setup Assistant.

An adapted Python script is used to command the pose of the robot in both Cartesian (end effector pose) and configuration space (joint angles). A rosnode is launched to apply the control on the robot in RViz. The ability of the controller to perform obstacle avoidance is tested by instantiating a box in RViz and placing it in a waypoint between the initial and target poses.

The trajectories were constructed using a pose randomization technique. For the target poses included in the robot's workspace, a trajectory was always found. When a box was added, the controller was still able to generate an alternative trajectory when the box was avoidable. The simulation time was longer in the latter case due to a higher number of sampled poses.

## Robot control simulation on Gazebo

Gazebo was used for simulating the real robot in a realistic environment, enabling to test and validate control algorithms and sensor integration. The HC10 robot was equipped with a ros controller and Gazebo packages to create a more realistic simulation environment. The robot's virtual world frame and joints' physical properties (inertia, friction, and damping) were added to the robot description file.

The trajectory planning was tested using a new effort controller. Obstacle avoidance was tested by adding a box in RViz, although the box was not visualized in Gazebo since it was not spawned from a physical model. However, the box's space was taken into account in the scanner or the trajectory.


## Sensors integration and perception pipeline

In this approach, the pipeline sensor was used to use octomap for a camera, in this case a Kinect. The integration of a 3D sensor like the Kinect allowed for mapping of the environment, which can be useful for tasks such as object recognition, manipulation, and quality control. It also enhances the robot's ability to perceive and manipulate the surrounding environment in 3D space, opening up new possibilities for industrial applications such as bin-picking, object recognition, and quality control.

Note that the boxes included in Gazebo are not visualized in RViz and the boxes in RViz are not visualized in Gazebo, but they are taken into account in the scanner or the trajectory.

