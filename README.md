# ROS Turtlebot Walker - ENPM808X
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Project Overview

This package implements a Roomba cleaning robot type behavior using the turtlebot platform in ROS. It also caontains a simulation demo in Gazebo.

## Dependencies
The project has the following dependencies.

1. ROS Kinetic ([Installation](http://wiki.ros.org/kinetic/Installation))
2. catkin ([Installation](http://wiki.ros.org/catkin#Installing_catkin))
3. Turtlebot Packages
```
sudo apt-get install ros-kinetic-turtlebot-*
```

## Build steps
 
- To build the given project, create and build the catkin workspace by following the given steps:
```
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin_make
source ~/catkin_ws/devel/setup.bash
cd src/
git clone --recursive https://github.com/rohansingh42/turtlebot_walker.git
cd ~/catkin_ws/
catkin_make
```

- NOTE: For running command from each new terminal, source the devel/setup.bash file in every new terminal before executing any ros command, or add the following line to your _~/.bashrc_ once
```
source ~/catkin_ws/devel/setup.bash
```

## Running the demo

- To run the simulation demo using the launch file (after sourcing _devel/setup.bash_ according to above note), in a new terminal type,
```
roslaunch turtlebot_walker walkerDemo.launch record:=<true/false> record_time:=<recording duration in secs>
```
The default values for the params _record_ (whether to record or not) and _record_time_ (how long to record) are _false_ and _30_ respectively. The recorded bag files are saved in the _results_ subdirectory.

- To just run the node with the walker algorithm, type in a new terminal,
```
rosrun turtlebot_walker walker
```

## Viewing data

- To view rosbag file information, type in a new terminal,
```
rosbag info results/<name of bagfile>
```
Assuming tha command is run from base directory. If not, give relative path to bag file from current directory.

- To replay the recorded bag file, type in a new terminal (after running roscore),
```
rosbag play results/<name of bagfile>
```
Assuming tha command is run from base directory. If not, give relative path to bag file from current directory.

- To check the published message commanding the turtlebot, type in a new terminal (after running the demo or the rosbag),
```
rostopic echo /cmd_vel_mux/input/navi
```
