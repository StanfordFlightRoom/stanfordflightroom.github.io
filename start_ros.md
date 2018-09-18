---
permalink: start_ros
title: "Robot Operating System (ROS) Quick Start Guide"
layout: "single"
sidebar:
  nav: "docs"
---

### What is ROS?
The [Robotic Operating System (ROS)](http://www.ros.org/about-ros/) is a collection of software that facilitates robotics. Most notably, it enables communication between multiple networked devices (robots) without the need for low-level networking. We use ROS in the flight room to communicate all sensing and control data between computers and robots. 

### How do I use ROS?
* Familiarize yourself with the basic [ROS tutorials](http://wiki.ros.org/ROS/Tutorials) (independent of the flight room)
* Setup [Local Hostnames](/setup_local_hostnames)
* Ensure that you can communicate with the flight room's [ROS core](/setup_computers) by setting the following in terminal
```bash
$ export ROS_MASTER_URI = http://relay.local:11311
$ export ROS_HOSTNAME = $HOSTNAME.local
```
* Hint: add these commands to your `~/.bashrc` which will execute each time you start a new bash session

### How do I read data from Optitrack on my personal computer (or robot)?
Refer to [Reading Data with ROS](/motion_capture_ros)