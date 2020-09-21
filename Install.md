
# **MIP robotics**

## **Installation** for **ROS Melodic** and **Gazebo**

### Install ROS melodic

#### Install Melodic ROS following the tutorial:

&nbsp; &nbsp; http://wiki.ros.org/melodic/Installation/Ubuntu

#### Or follow these instructions : (execute one group at a time)

Key setup
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
```
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654

```

Check for updates

```
sudo apt update
```

Install full ROS melodic version

```
sudo apt install ros-melodic-desktop-full
```

set melodic as main ROS distribution on system

```
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### Creating a workspace

Creating a workspace to store all data

```
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin_make
```
catkin_ws can be changed to any directory name

### Adding extra packages

Install the following packages:
```
sudo apt install ros-melodic-joint-state-publisher-gui \
 ros-melodic-gazebo-ros-pkgs \
 ros-melodic-ros-controllers \
 ros-melodic-ros-control \
 ros-melodic-gazebo-ros-control \
 rospack-tools
```

### Installing MoveIt!

http://docs.ros.org/melodic/api/moveit_tutorials/html/doc/getting_started/getting_started.html

or follow these :

Update ROS dependencies
```
rosdep update
sudo apt-get update
sudo apt-get dist-upgrade
```

Check tools are installed
```
sudo apt-get install ros-melodic-catkin python-catkin-tools
```

Install MoveIt!
```
sudo apt install ros-melodic-moveit
```
### Install Trac_IK

Trac_IK is an inverse kinematic solver for 4 and 5 degrees of freedom

http://docs.ros.org/melodic/api/moveit_tutorials/html/doc/trac_ik/trac_ik_tutorial.html

or

```
sudo apt-get install ros-melodic-trac-ik-kinematics-plugin
```

### install Grasp fix plugin

```
sudo apt-get install \
    ros-melodic-gazebo-ros \
    ros-melodic-eigen-conversions \
    ros-melodic-object-recognition-msgs \
    ros-melodic-roslint
```

Once those installation completed, download all the packages from the github folder into the src folder of your catkin_ws.

--------------------------

## First time init

The very first time you launch this you will have to go through these instructions

### Add all necessary files

If you haven't added the files into the src folder please do.

### make workspace

go to your workspace directory
```
cd ~/catkin_ws
```

Make directory
```
catkin_make
```

catkin_make is required after every changes that a performed to compile them into a valid application.


### launch moveit

In another terminal, source and launch Gazebo:
```
cd ~/catkin_ws
source devel/setup.bash
roslaunch mip_junior_300_moveit mip_junior_300_gazebo_objects_controlled.launch
```
This launch file will:
- launch our world in gazebo
- spawn the robot
- load the controllers defined in ros_controllers.yaml
- run the controller spawner

Notes :
- it will take a while (4-5 minutes)
- there will be a lot of red and orange on the screen
- recommended to go get a coffee at this point
