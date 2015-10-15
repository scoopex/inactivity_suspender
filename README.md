inactivity_suspender
====================

inactivity_suspender - a quick ruby hack for suspending your home server

I use my linux system at home to be:
 * a regular workstation
 * a media server
 * a file server

I wakeup the system by using "Wake On Lan" by using: 
 * Linux - "etherwake"
 * Android - "Wake on Lan", https://play.google.com/store/apps/details?id=at.increase.wakeonlan
 * Fritzbox automatic "Wake on Lan" feature on port connection attempt
 * XMBC/OpenElec - "Advanced_Wake_On_Lan" Add-on
 
Therefore i do not want to automatically suspend it when a download is in progress, media i served to the local network of someone uses the fileserver.
Typical linux suspend mechanisms do not care for network things.

I wrote this quick ruby hack as a workaround.
(I love linux for having the possibility to write such a easy hack...)

# What it does

 * Check if there is some network activity beyond a specified transferrate
 * Check if there is no mouse activity within a defined interval
 * Check is there currently not at least a specified number of disk operations are in progress for 10 seconds

If this is all true, suspend the system.

# How to use it

* Install the tool
```
cd /opt
git clone git@github.com:scoopex/inactivity_suspender.git
```
* Put the following line to /etc/rc.local and add additional arguments if necessary
```
/usr/bin/screen -S inactivity_suspender -d -m  bash -c '/opt/inactivity_suspender/inactivity_suspender'
```
* How to check whats going on
```
sudo bash
screen -x inactivity_suspender
```

# TODO

- Change ops to ops/10sec to ops/sec limit
