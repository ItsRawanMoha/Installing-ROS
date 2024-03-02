# Step-by-step guide to install ROS (Robot Operating System):

## Step 1: Setting up Jetson nano 
<img src="https://github.com/ItsRawanMoha/Installing-ROS/blob/main/image%20(16).png" alt="Alt text" width="325" height="200">

Jetson Nano is typically connected using various interfaces for development and usage. For setting up:

- microSD card slot for main storage
- 40-pin expansion header
- Micro-USB port for Device Mode
- Gigabit Ethernet port
- USB 2.0 ports (x2)
- USB 3.0 port (x1)
- HDMI output port
- USB-C for 5V power input
- MIPI CSI-2 camera connector

<img src="https://github.com/ItsRawanMoha/Installing-ROS/blob/main/image%20(15).png" alt="Alt text" width="600" height="400">

## Step 2: Write Image to the microSD Card
1- Format your microSD card using SD Memory Card Formatter from the SD Association.

![screen-gif](https://github.com/ItsRawanMoha/Installing-ROS/blob/main/image%20(17).png)

2- Use Etcher to write the Jetson Nano Developer Kit SD Card Image to your microSD card.

 ![screen-gif](https://github.com/ItsRawanMoha/Installing-ROS/blob/main/image%20(18).png)

## Step 3: Installing ROS
ROS Melodic installation instructions for ubuntu 
### 1- Configure your Ubuntu repositories
Configure your Ubuntu repositories to allow "restricted," "universe," and "multiverse." You can follow the Ubuntu guide for instructions on doing this.

### 2- Setup your sources.list
Setup your computer to accept software from packages.ros.org.
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
### 3- Set up your keys
```
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```
- Installation
First, make sure your Debian package index is up-to-date:
```
sudo apt update
```
Now pick how much of ROS you would like to install.

- Desktop-Full Install: (Recommended) : ROS, rqt, rviz, robot-generic libraries, 2D/3D simulators and 2D/3D perception
```
sudo apt install ros-melodic-desktop-full
```

- Desktop Install: ROS, rqt, rviz, and robot-generic libraries
```
sudo apt install ros-melodic-desktop
```

- ROS-Base: (Bare Bones) ROS packaging, build, and communication libraries. No GUI tools.
```
sudo apt install ros-melodic-ros-base
```

Individual Package: You can also install a specific ROS package (replace underscores with dashes of the package name):
```
sudo apt install ros-melodic-PACKAGE
```
e.g.
```
sudo apt install ros-melodic-slam-gmapping
```
To find available packages, use:
```
apt search ros-melodic
```
### 4- Environment setup

It's convenient if the ROS environment variables are automatically added to your bash session every time a new shell is launched:

```
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

If you have more than one ROS distribution installed, ~/.bashrc must only source the setup.bash for the version you are currently using.
If you just want to change the environment of your current shell, instead of the above you can type:
```
source /opt/ros/melodic/setup.bash
```
If you use zsh instead of bash you need to run the following commands to set up your shell:
```
echo "source /opt/ros/melodic/setup.zsh" >> ~/.zshrc
source ~/.zshrc
```

### 5- Dependencies for building packages

Up to now you have installed what you need to run the core ROS packages. To create and manage your own ROS workspaces, there are various tools and requirements that are distributed separately. For example, rosinstall is a frequently used command-line tool that enables you to easily download many source trees for ROS packages with one command.

To install this tool and other dependencies for building ROS packages, run:

```
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```

### 6- Initialize rosdep
Before you can use many ROS tools, you will need to initialize rosdep. rosdep enables you to easily install system dependencies for source you want to compile and is required to run some core components in ROS. If you have not yet installed rosdep, do so as follows.

```
sudo apt install python3-rosdep
```
With the following, you can initialize rosdep.

```
sudo rosdep init
rosdep update
```

### Step 6: To start the ROS (master node)

```
$ roscore
```
![screen-gif](https://github.com/ItsRawanMoha/Installing-ROS/blob/main/image%20(20).png)

If ROS is installed correctly, you should see output indicating that the ROS master is running.

That's it! You've successfully installed ROS on your Ubuntu system. You can now start using ROS for robotics development and experimentation.
