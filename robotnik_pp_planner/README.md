# robotnik_pp_planner

## 1 - robotnik_pp_planner_node

Component that performs the pure pursuit navigation. Valid for Ackermann and Differential odometries.

### 1.1 - Params

* position_source (string)
 * Sets whether to use the global /map reference or the robot's odometry
 * MAP to use the /map frame
 * ODOM to use the /odom frame
* target_frame (string)
 * base frame used to refer the navigation
* d_lookahear_min (double)
 * minimum lookahead used in the algorithm
* d_lookahear_max (double)
 * maximum lookahead used in the algorithm
* kr (double)
 * constant used in the algorithm
* command_type (string)
 * sets the type of command to use depending on the robot odometry type
 * Twist for geometry_msgs/Twist
 * Ackermann for ackermann_msgs/AckermannDriveStamped
* odom_topic (string)
 * topic to read the robot's odometry
* cmd_topic_vel (string)
 * name topic to command the robot
* desired_freq (double)
 * control thread frequency of the controller (recommended 100 Hz)
 
### 1.2 - Topics
 
#### 1.2.1 Subscribers
* /odom_topic (nav_msgs/Odometry)
 * gets the robot's odometry
 
#### 1.2.2 - Publishers
 
* /cmd_topic_vel (ackermann_msgs/AckermannDriveStamped or geometry_msgs/Twist)
 * publishes the velocity commands to command the robot
 
### 1.3 - Simple Action Server
* /robotnik_pp_planner/* (robotnik_pp_msgs/GoToAction) 
 * accepts actions to follow a set of waypoints 

### 1.4 - Bringup


```
$> roslaunch robotnik_pp_planer purepursuit.launch
```

## 2 - path_marker.py

ROS node that creates [Interactive Markers](http://wiki.ros.org/interactive_markers) to create several waypoints and send them to the planner_node

### 2.1 - Params

* frame_id (string)
 * frame to reference the markers and the created waypoints
* planner (string)
 * name of the action service to connect with

### 2.2 - Bringup

```
$> roslaunch robotnik_pp_planer purepursuit_marker.launch
```
