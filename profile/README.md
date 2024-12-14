# DormDash - README
 
Welcome to the GitHub organization profile for Fall 2024 Undergraduate Group 9’s Senior Design Project at San José State University’s Department of Computer Engineering.

## Overview of source code

Please see the [repository list](https://github.com/orgs/DormDash-SJSU/repositories) to see details on all of our source code.

Our repositories consist of the following:

- ROS workspace with submodules representing all packages used [(link)](https://github.com/DormDash-SJSU/ws)
- Arduino source code for robot’s food box locking mechanism [(link)](https://github.com/DormDash-SJSU/DormDash-Locking-Box)
- Scripts used to perform data collection and analysis [(link)](https://github.com/DormDash-SJSU/DormDash-Analysis)
- ROS packages for core robot functionality (see [repository list](https://github.com/orgs/DormDash-SJSU/repositories))

## Building and running

This project has a complex software stack consisting of various components that correspond to different aspects of the robot. These instructions are divided into sections, one for the ROS-based software, and another for the Arduino-based software for the robot’s food box.

### ROS-based software

#### Building

1. Install ROS 2 Humble Hawksbill on Raspberry Pi per [instructions](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debs.html) (requires Ubuntu 22.04 LTS)

2. Set up Yahboom ROS Expansion Board as a serial device on Raspberry Pi, and install Yahboom Python driver library per [Yahboom documentation](http://www.yahboom.net/study/ROS-Driver-Board)

3. Clone our ROS workspace respository
<br>`cd && git clone --recurse-submodules https://github.com/DormDash-SJSU/ws.git`

3. Build the workspace
<br>`cd ~/ws && colcon build && source install/setup.bash`

4. Install dependencies
<br>`sudo apt install ros-humble-v4l2-camera python-is-python3; pip install -r requirements.txt`

All ROS packages are now built, and dependencies necessary for running them are installed.

#### Running

1. Start the `v4l2_camera` node
<br>`ros2 run v4l2_camera v4l2_camera_node`

2. In a new terminal, start the LiDAR node
<br>`ros2 run pkg_lidar_py lidar`

3. In a third terminal, start the GPS node
<br>`ros2 run ros_gps_pub gps_publisher`

4. In a fourth terminal, start the `darknet_ros` node
<br>`ros2 launch darknet_ros darknet_ros.launch.py`

### Arduino-based software

#### Building

1. Create a new sketch in the Arduino IDE on your computer

2. Replace the code in the code editor with the contents of [the Arduino source file](https://github.com/DormDash-SJSU/DormDash-Locking-Box/raw/refs/heads/main/keypad.ino)

3. While Arduino is connected via USB, click the “Upload” button in Arduino IDE

The locking mechanism’s firmware is now flashed onto its microcontroller unit.

#### Running

1. Refer to instructions in the README of the [DormDash Locking Box repository](https://github.com/DormDash-SJSU/DormDash-Locking-Box) to operate the software

## Performing data collection and analysis

We wrote Python scripts to measure the performance of object detection and key sensors in the robot, as well as to analyze and plot the data. Instructions to replicate our methodology is as follows:

1. On the Raspberry Pi, clone the [data analysis repository](https://github.com/DormDash-SJSU/DormDash-Analysis)
<br>`git clone https://github.com/DormDash-SJSU/DormDash-Analysis.git`

2. Install dependencies
<br>`cd DormDash-Analysis && pip install -r requirements.txt`

3. Build and run the ROS-based software per [instructions](#ros-based-software)

4. Run data analysis
<br>`python fps_analyzer.py && python lidar_analyzer.py`

This will generate CSV files with gathered data.

5. Plot results
<br>`python fps_plot.py && python lidar_plot.py && python lidar_plot2.py`

This will generate SVG files with plots.
