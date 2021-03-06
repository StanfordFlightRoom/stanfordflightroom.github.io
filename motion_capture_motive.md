---
permalink: motion_capture_motive
title: "Motive Software Setup and Usage"
layout: "single"
sidebar:
  nav: "docs"
---

## Preliminary
* Turn on the `mocap` computer and the power strip in the flight room to power the cameras and router for the local network (shown below)
* Open Motive on the `mocap` computer
* Select the layout entitled `FlightRoomLayout` in the upper-right corner of Motive to display the standard window configuration

<p style="text-align:center;">
<img src="assets/flightroom_switches.jpg" width="500"/>
</p>

## Calibration
Calibrating the Optitrack system refers to the process of identifying the intrinsic and extrinsic parameters of each camera in the network. This process requires maneuvering the calibration wand around the environment to collect multiple images of the wand from each camera. Motive performs an optimization on this data to estimate the parameters. After this step, other objects in the space may be triangulated from the known camera poses. 

Calibration should only be completed if there is significant tracking error or your experiment requires extreme precision. Refer to the video below to calibrate the system. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/cNZaFEghTBU" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## Coordinate Frames in Optitrack
The world coordinate frame in Optitrack is determined by setting the ground plane in the calibration. By default, this coordinate system is defined as in the image below. 

<p style="text-align:center;">
<img src="assets/mocap_coodinate_system.png" width="500"/>
</p>

## Setup Rigid Bodies
Rigid bodies are defined by a set of retro-reflective markers attached to the objects in the flight room. These markers are available to everyone on the flight room's desk. **Please** handle the markers with care! Damaging the markers will seriously degrade the performance of the system for all users. Try not to touch the markers with your bare skin as the oils on your hands can reduce the reflective property of the markers. 

Refer to the video below to define rigid bodies in Motive. 
<iframe width="560" height="315" src="https://www.youtube.com/embed/Z9kO7jJgCLE" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

Rigid bodies, or `assets`, are labeled by their name. This information can be accessed and modified through the `Asset` pane as shown below. 

<p style="text-align:center;">
<img src="assets/mocap_assets.png" width="400"/>
</p>

## Optitrack Troubleshooting Guide 
1. **The system won't acquire wanding points for calibration**: ensure the wand markers are not damaged, you are not wearing anything reflective for the system, and that the markers are physically in the correct position on the calibration wand (in the `A` configuration). 
2. **The cameras will not appear up in Motive**: power cycle the entire system (switches, router, and `mocap` computer). 
3. **A camera stopped transmitting data**: first try power cycling the entire system. If that doesn't work you should report the problem. In the meantime, simply calibrate without that camera and use the system as normal (it should still be quite accurate). 


