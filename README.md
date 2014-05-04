inactivity_suspender
====================

inactivity_suspender - a quick ruby hack for suspending your home server

I use my linux system at home to be:
 * a regular workstation
 * a media server
 * a file server

Therefore i do not want to automatically suspend it when a download is in progress, media i served to the local network of someone uses the fileserver.
Typical linux suspend mechanisms do not care for network things.

I wrote this quick ruby hack as a workaround.
("I love linux")

# What it does

 * Check if there is some network activity beyond a specified transferrate
 * Check if there is no mouse activity within a defined interval
 * Check is there currently not at least a spcified number of disk operations are in progress

If this is all true, suspend the system.

# How to use it

* Install the tool
```
cd /opt
git clone git@github.com:scoopex/inactivity_suspender.git
```
* Put the follwing line to /etc/rc.local and add additional arguments if neccessary
```
/usr/bin/screen -S inactivity_suspender -d -m  bash -c '/opt/inactivity_suspender/inactivity_suspender'
```
* How to check whats going on
```
sudo bash
screen -x inactivity_suspender
```
