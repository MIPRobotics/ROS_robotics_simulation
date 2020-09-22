
# **MIP robotics**

# Create new workspace

Create a new_folder which will be the new workspace

Inside create a folder named src

Go to the new_folder and right mouse click inside the file directory of the new_folder and click on "open new terminal"

Inside this new terminal type
```
git clone https://github.com/MIPRobotics/ROS_robotics_simulation folder -src
```
and
```
catkin_make
```

## **Execution** commands for **ROS1** and **Gazebo**

On the first terminal:
```
source devel/setup.bash
roslaunch mip_junior_300_moveit mip_junior_300_gazebo_objects_controlled.launch
```

After Gazebo is launched enter on a second terminal:
```
source devel/setup.bash
roslaunch mip_junior_300_moveit mip_junior_300_moveit.launch
```

In rviz a cyan ball appears inside the end effector use the ball to move the arm inside rviz to the appropriate point.

Once done inside the **MotionPlanning** in the **Planning** tab click on **Plan and Execute**, the robot should be moving.
