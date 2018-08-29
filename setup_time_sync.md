---
permalink: setup_time_sync
title: "Using the Local Time Server"
sidebar:
  nav: "docs"
---

Many embedded computers (such as the ones on drones or mobile robots) do not have a real-time clock that maintains the correct time between power cycles. For some applications, such as visualizing sensor data from multiple robots using ROS, the clocks for the robots need to be synchronized in order to properly visualize the data in RVIZ. 

Typically, computers also use the internet to periodically adjust the clock. However, the Flight Room network does not have general internet access, in accordance with Stanford IT rules. Therefore, one of the computers in the Flight Room has been configured so that devices can receive the correct (internet) time. 

## Network Time Protocol (NTP) Setup

The Network Time Protocol (NTP) allows for time synchronization to within a few milliseconds of Coordinated Universal Time (UTC) using a client-server model. You will need administrator privileges to install the service and modify a configuration file.

### Ubuntu 16.04 / 18.04

Install the service by running `sudo apt-get install ntp` in a terminal. After installation, open the configuration file `etc/ntp.conf` with administrator privileges using your favorite text editor. 

To add the computer `relay` as an NTP resource using .local hostnames (see [Local Hostnames](/setup_local_hostnames)), add `server relay.local iburst` to the configuration file,
```
...
# Specify one or more NTP servers.
server relay.local iburst
...
```
Running `ntpq -p` shows the servers being used for time synchronization and correction.
```bash
$ ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*relay.local     45.33.48.4       3 u   40   64    1    6.670   -3.943   1.491
 0.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 1.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 2.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 3.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 ntp.ubuntu.com  .POOL.          16 p    -   64    0    0.000    0.000   0.000
```
Issues with NTP are usually resolved by restarting the service with `sudo service ntp restart` (or simply rebooting).

## Resources
[ntp configuration reference](http://doc.ntp.org/4.1.1/confopt.htm)
[ntpq program reference](http://doc.ntp.org/4.1.0/ntpq.htm)