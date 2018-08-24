---
permalink: motion_capture_motive
title: "Using Optitrack's Motive and Getting Data"
layout: "single"
sidebar:
  nav: "docs"
---

Data Streaming Pane
1. Go to View ­> Data Streaming Pane
2. Set Broadcast Frame Data to Off/. Set all switches to off, except for Rigid Bodies, which
should be turned on.
3. Set Broadcast VRPN Data to On.

Access Streaming Data
1. Open terminal on both computers. Computer 1 will be the one running Motive. Computer 2 will be the one receiving data.
2. Computer 1: ‘roscore’
3. Open new terminal and launch VRPN client: ‘roslaunch vrpn_client_ros sample.launch’
4. Computer 2: ‘rostopic list’
a. The following error might be produced: “ERROR! Cannot communicate with master.”
i. Computer 1: ‘nano ~/.bashrc’
ii. Computer 2: ‘source .bashrc’
iii. Type export statements from Computer 1 at the end of the bashrc file on Computer 2 except the HOST_NAME command