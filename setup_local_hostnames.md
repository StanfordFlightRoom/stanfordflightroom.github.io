---
permalink: setup_local_hostnames
title: "Using .local Hostnames"
sidebar:
  nav: "docs"
---
A hostname is a name assigned to a device on a network to more easily distinguish between devices instead of using a string of numbers (IP addresses). IP addresses may also be dynamically assigned, making it difficult to consistently reference the same device. 

Hostnames can be resolved on the Flight Room network without using a custom DNS or specifying static IP addresses through the router. All devices connected to the network must be running a Zero Configuration Networking (Zeroconf) service which then allows any device to be referenced by adding `.local` to its hostname.

**Each device should have a unique hostname!**

## Example
One computer uses the hostname `hal` and another uses the hostname `marvin`. If both run a Zeroconf service and are on the same network, then `hal` contacts `marvin` using the address `marvin.local`, e.g.
```bash
$ ping marvin.local
$ ssh username@marvin.local
```

## Zeroconf and ROS
Using the `.local` hostname also works with ROS. On Ubuntu, specify `marvin` as the ROS Master with
```bash
$ export ROS_MASTER_URI = http://marvin.local:11311
```
and specify the computer's ROS hostname using
```bash
$ export ROS_HOSTNAME = $HOSTNAME.local
```
Add both commands  to a user's `.bashrc` file to simplify setup. 

## Setting up the service
You will need administrator privileges if the service is not already installed. 

### Ubuntu 16.04 / 18.04
A standard installation of Ubuntu will already have a Zeroconf service running, called `avahi`. Check the status by running `service avahi-daemon status` in a terminal.
```bash
$ service avahi-daemon status
● avahi-daemon.service - Avahi mDNS/DNS-SD Stack
   Loaded: loaded (/lib/systemd/system/avahi-daemon.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2018-08-28 10:09:34 PDT; 53min ago
 Main PID: 1773 (avahi-daemon)
   Status: "avahi-daemon 0.7 starting up."
    Tasks: 2 (limit: 4915)
   CGroup: /system.slice/avahi-daemon.service
           ├─1773 avahi-daemon: running [msladam.local]
           └─1784 avahi-daemon: chroot helper
```
Otherwise, the package is available in the standard Ubuntu repositories and is installed (or updated) with `sudo apt-get install avahi-daemon`. A simple check of the service is running 
```bash
$ ping $HOSTNAME.local
```
and making sure the address resolves successfully. If the the hostname does not resolve, try the following:  
1. Install the `avahi` packages:
```bash
sudo apt-get install avahi-daemon avahi-dnsconfd avahi-discover avahi-utils
```  
2. Install `libnss-mdns`:
```bash
sudo apt-get install libnss-mdns
```
3. Check that `/etc/nsswitch.conf` has the following line:  
```
hosts:    files mdns4_minimal dns [NOTFOUND=return] mdns4
```

Restart `avahi` with `sudo service avahi-daemon restart` and try resolving .local hostnames.

### Windows 10
Some applications ship with a Zeroconf service called `bounjour` including Skype and iTunes. Otherwise, the easiest way to install `bounjour` is to install iTunes. If you don't want to install iTunes, download the iTunes installer and extract it using 7-Zip or WinRAR. There should be a separate `bonjour` installer in the extracted files. 

Check the service by running
```console
> ping %COMPUTERNAME%.local
```
in a command prompt. 

## Changing hostnames

[For Ubuntu](https://www.cyberciti.biz/faq/ubuntu-change-hostname-command/)  
[For Windows](https://kb.iu.edu/d/ajnx)

## Resources
[ROS Network Setup](http://wiki.ros.org/ROS/NetworkSetup)




