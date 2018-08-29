---
permalink: setup_ros_upstart
title: "Starting ROS packages on startup"
sidebar:
  nav: "docs"
---

Often times it is useful to start a ROS package when a robot boots up. For example, the `relay` computer in the Flight Room (see [Lab Computers](/setup_computers)) starts a ROS core on boot for devices on the local network. This functionality is achieved using the [robot_upstart](http://wiki.ros.org/robot_upstart) package. 

On `relay`, the service is called `ros_startup`. Check the status with the command `service ros_startup status`. 

## Install robot_upstart

### Ubuntu 16.04 / 18.04

The package is available through `apt` and can be installed with `sudo apt-get install ros-kinetic-robot-upstart` for ROS Kinetic. Otherwise, clone the source repository into a Catkin workspace and build it from source. If building from source, also install the Ubuntu package `daemontools` with `sudo apt-get install daemontools`. 

## Using robot_upstart

Using `robot_upstart` is simple and is explained on the [robot_upstart documentation page](http://docs.ros.org/jade/api/robot_upstart/html/).

To have the launch file `launch/example.launch` from the ROS package `example_package` run on computer startup, use the command
```bash
$ rosrun robot_upstart install example_package/launch/example.launch
```
A service called `example` will be created. Use the `--job` flag to provide a custom name, otherwise it will be constructed from the package name. Check the service status with
```bash
$ service example status
```
Launching an empty launch file (i.e. only containing `<launch></launch>`) will still create a ROS core if no ROS core is running.