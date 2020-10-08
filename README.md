# MIP-robotics : Making robotics accessible to all

## Our vision

**MIP-robotics** whishes to help create a **world** where **industrial robotics is accessible to all**.

To that effect we have developped :
- A drag and drop web interface
- Constructed a simulated environnement to check the programs validity
- Supplemented our robot with a tablette for fine tuning movements
- Seemless integration to cobot for direct physical execution

For more advanced users we have built natively our cobot on ROS, this provides many advantages among others:
- ROS is a popular ecosystem for robotics in the world from hobbist to academia and industry, all are familiar with it.
- it allows simple integration of third party sensors and actuators with ROS drivers.
- Robots can even become a PLC increasing your ROI

##  Sample code

This repositary contains a **glimps of our cobots capabilities**, we demonstrate here basic funtionalities such as **motion within a simulated environnement**, to access all functionalities give us a call.

This sample shows a MIP Junior 300 moving inside a Gazebo simulation taking commands from the MoveIt! planner, the planner is controlled by the user through the displacement of a ball within rviz.

The goal is for you to modify the simulation to represent your environement, and to help you decide if our cobot is well suited to your application inside your factory.

Example of existing client applications :
- Taking or putting and object form a conveyor into a cnc machine
- Bringing a heavy object to an operator to decrease TMS(repetitive stress inguries)
- Depositing a liquid onto a component
- Soldering points on a plane
- Screwing lids on tonno
- Unpacking and packing palettes
- etc...

These are some of many examples that could be futher enriched by your application.

If you are interested in more information or indepth integration, please contact us at :
add contact URL

## What to expect

Disclaimer :
This repos is a sample code with limited functionalities, for the full list of our cobots functionnalities please contact us.   

This sample contains the simulation and motion performed by our cobot.

## Using this sample code

This sample code will require several dependencies :
- a multicore computer
- it is recommended to have a dedicted graphics card
- Linux Ubuntu 18.04
- ROS Melodic
- MoveIt! Melodic
- Gazebo
- other misc packages

To ensure proper installation, please follow all the installations steps bellow.

## Installation of sample code

### Install ROS melodic

#### Install Melodic ROS following the tutorial:

&nbsp; &nbsp; http://wiki.ros.org/melodic/Installation/Ubuntu

#### Or follow these instructions : (execute one group at a time within a terminal)

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

Install ROS melodic

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

Trac_IK is an inverse kinematic solver for 4 and 5 degrees of freedom robots

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

## First time init

The very first time you launch this you will have to go through these instructions

### Add all necessary files

If you haven't added the files into the src folder please do.

### Make workspace

Go to your workspace directory
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
- launch a world in gazebo
- spawn the robot
- load the controllers defined in ros_controllers.yaml
- run the controller spawner

Notes :
- it will take a while (4-5 minutes)
- there will be a lot of red and orange on the screen
- recommended to go get a coffee at this point

## Execution of sample code

### Create new workspace

Create a new_folder which will be the new workspace

Go to the new_folder and right mouse click inside the file directory of the new_folder and click on "open new terminal"

Inside this new terminal type
```
git clone https://github.com/MIPRobotics/ROS_robotics_simulation src
```
and
```
catkin_make
```

#### **Execution** commands for **ROS1** and **Gazebo**

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

## Personnalisation of the world

Personnalization of the world can be done by editing the world file and adding new models within Gazebo.

If you need some help please contact our team we will be glad to help you.
