# Junior package
This package defines junior robot.



## Demo
In every terminal you open, you have to source:
```
source /opt/ros/melodic/setup.bash
```
Or it can be done automatically if you add it to bashrc:
```
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

-----------------------------------
Then, in another terminal to compile:
```
cd ~/catkin_ws
catkin_make
```

Source and launch one of the launch files:
```
source devel/setup.bash
roslaunch junior <launch_file_name>
```
Launch files are explained below or on top of each launch file.


## Config folder
junior_joints_control.yaml defines junior's controllers. These controllers control the joints.

## Launch folder
- just_rviz.launch: displays Junior in Rviz. Joints values can be changed with the user interface.

- just_gazebo.launch: displays Junior in Gazebo. Joints values can't be controlled, robot's joints can't be moved.
- gazebo_junior_control.launch: displays Junior in Gazebo. Joints values can be controlled via controllers.
For example, to move m2, write in the terminal:
```
rostopic pub /junior/m1_to_m2_position_controller/command std_msgs/Float64 "data: 1.0"
```  
Gripper's joints can't be controlled yet.
- urdf.rviz and urdf2.rviz: configuration files for Rviz.

## Meshes folder
Contains 3D stl files of robot's links.

## Urdf folder
Contains URDF or Xacro files. Description can be find at the top of each file.
