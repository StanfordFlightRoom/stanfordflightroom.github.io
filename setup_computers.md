---
permalink: setup_computers
title: "Laboratory Computers"
layout: "single"
sidebar:
  nav: "docs"
---

There are two computers set up in the Flight Room for use with the motion capture system and the local network.

## mocap

HP computer running Windows 10.  

* Hostname: `mocap`
* Runs Motive to interface with Optitrak system


## relay

Acer computer running Ubuntu 18.04.

* Hostname: `relay`
* Runs a ROS core on boot for devices on the local network (see [ROS Upstart](/setup_ros_upstart))
* Runs as a time synchronization server (see [Time Synchronization](/setup_time_sync))
* Can be rebooted remotely using `sudo reboot` (does not require administrator privileges)
