# RoboND-Robot-Map-My-World

Project 4 of Udacity Robotics Software Engineer Nanodegree Program [Video Clip](https://youtu.be/u6Ax9PQRKWU)


[![Demo_Video](/videos/RoboND-Robot-Map-My-World.gif)](https://youtu.be/u6Ax9PQRKWU)

## Overview  
In the Map My World project, the 2D occupancy grid, and 3D octomap are created in a simulated environment using Jetbot (mobile robot) with the RTAB-Map package.
RTAB-Map (Real-Time Appearance-Based Mapping) is a popular solution for SLAM to develop robots that can map environments in 3D. RTAB-Map has good speed and memory management, and it provides custom developed tools for information analysis. 
However, Jetbot model is very small can be driven **maximum at 0.l speed**.</br></br>
![Jetbot_Model2](images/jetbot_model_2_small.png)  

![Screen Shot2](images/2D_occupancy_grid_path_small.png) 

## Prerequisites/Dependencies  
* Gazebo >= 7.0  
* ROS Kinetic  
* ROS rtabmap_ros package  
```
sudo apt-get install ros-kinetic-rtabmap-ros
```

* ROS gazebo package  
```
sudo apt-get install ros-kinetic-gazebo-ros-pkgs ros-kinetic-gazebo-ros-control  ros-kinetic-effort-controllers
```

## Run the project  
* Clone ros-teleop repository
* Clone this repository
* Open the repository and make  
```
cd /home/catkin_ws/src
git clone https://github.com/ros-teleop/teleop_twist_keyboard
cd ..
catkin_make
```

* Launch my_robot in Gazebo to load both the world and plugins  
```
cd /home/workspace/catkin_ws/
source devel/setup.bash
roslaunch my_robot world.launch
```  
![Screen Shot1](images/gazibo_sim_small.png) 

* Launch RTAB-Map package  

Option 1: Delete database when launch startup.
```
cd /home/workspace/catkin_ws/
source devel/setup.bash
roslaunch my_robot mapping.launch
```  
Option 2: Not delete database when launch startup.
```
cd /home/workspace/catkin_ws/
source devel/setup.bash
roslaunch my_robot localization.launch
```  

* Launch ROS Teleop Twist Keyboard</br>
**IMPORTANT!!! Jetbot model is very very small must keep speed not more than 0.1 otherwise it will be CRASHED**
```
cd /home/workspace/catkin_ws/
source devel/setup.bash
roslaunch my_robot teleop.launch
```  
### Creating the map
Navigate robot Gazebo simulation with the Teleop terminal start by lower velocity. The goal gets three loop closures that will be sufficient for mapping the entire environment. 
![PointCloud Shot1](images/pointcloud_small.png) 


### Visualizing RTABMAP data
After a successful mapping we can evaluate the database with RTAB-Map's database viewer, that can be started with the following command:
Download the database from the my_robot to the local computer. [Link to download rtabmap.db](https://drive.google.com/file/d/1GiLPXxCMNAwcNP0wBklw8C7O_VvoNSE4/view?usp=sharing)
```
cp ./rtabmap.db ~/catkin_ws/src/my_robot/database/
rtabmap-databaseViewer ~/catkin_ws/src/my_robot/database/rtabmap.db
```  
![DatabaseView](images/rtabmap_db_1118.png)



