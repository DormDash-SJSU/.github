# DormDash - README
 
Welcome to the GitHub organization for Undergraduate Group 9’s Senior Design Project at San José State University’s Department of Computer Engineering.

## Overview of source code

Our repositories consist of the following:

- ROS workspace with submodules representing all packages used
- ROS packages for core robot functionality
- Source code for robot’s food box locking mechanism
- Scripts used to perform data collection and analysis

## Building

1. Install ROS 2 Humble Hawksbill on Raspberry Pi per [instructions](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debs.html) (requires Ubuntu 22.04 LTS)

2. Set up Yahboom ROS Expansion Board as a serial device on Raspberry Pi, and install Yahboom Python Driver Library per [Yahboom documentation](http://www.yahboom.net/study/ROS-Driver-Board)

3. Clone our ROS workspace respository
<br>`cd && git clone https://github.com/DormDash-SJSU/ws.git`

3. Build the workspace
<br>`cd ~/ws && colcon build && source install/setup.bash`
