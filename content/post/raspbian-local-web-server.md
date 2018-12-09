---
title: "Raspbian Local Web Server"
date: 2018-11-27T20:43:35+02:00
draft: true
---

Go to https://www.raspberrypi.org/downloads/raspbian/ and download `Raspian Stretch With Desktop`

As at the time of writing, the version raspbian is `November 2018`

I then followed instructions found here https://www.raspberrypi.org/documentation/installation/installing-images/linux.md

lsblk will list information on available block devices, like hard drives and usbs

i redirect output to grep with -v to exclude snap routes

`lsblk | grep -v 'snap'` see screenshot for output


i then use this command to unzip and copy the raspbian image (**2018-11-13-raspbian-stretch.zip**) to the usb mounted micro sdcard located in `/dev/sda`

`unzip -p 2018-11-13-raspbian-stretch.zip | sudo dd of=/dev/sda bs=4M conv=fsync status=progress`

turn on pi, follow on screen prompts

terminal

`sudo apt update`
`sudo apt upgrade`


sudo apt list --installed | grep -i apache

months from 0-11 not 1-12
var d = new Date(year, month, day, hours, minutes, seconds, milliseconds);