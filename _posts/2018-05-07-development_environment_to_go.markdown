---
layout: post
title:      "Development Environment To Go!"
date:       2018-05-07 17:33:00 -0400
permalink:  development_environment_to_go
---


I've been toying around with my Raspberry Pi lately, trying to find some different (yet simple) things to do with it when I came across a way to access the Pi remotely over the internet. This gave me enough reason to try to set up a lightweight development environment entirely on the Pi and attempt some programming via my phone on the go. With a few simple tweaks and work-arounds, I got it up and running! 

The steps below are roughly how I got this set up. I'm working with a Raspberry Pi 3 running Raspbian Stretch as the OS on a 32gb SD card. Visit [raspberrypi.org](https://www.raspberrypi.org/) to learn more about their products. 

## Step 1: Operating System

I recommend using NOOBS to install Raspbian  - it's super simple. Instructions on using NOOBS can be found  [here](https://www.raspberrypi.org/documentation/installation/installing-images/).

Of course, you can install any number of compatible operating systems, including my go-to: Ubuntu MATE. Check out [these options](https://www.raspberrypi.org/downloads/) if you'd prefer to use something else!

## Step 2: Remote Access

I recommend this step next, as it's easier for me to do the rest of the setup while controlling the Pi from my laptop, but you can perform this step at any point. 

Note: you'll need to connect the Pi to a display and mouse/keyboard directly to perform the initial setup. After the tools are installed and the Pi is connected to the internet (wired or Wi-Fi), you can control it remotely without needing to be connected to a display, mouse, or keyboard. 

Once you have your operating system installed, setting up remote access is as easy as following [these directions](https://www.realvnc.com/en/connect/docs/raspberry-pi.html). 

## Step 3: Local Environment Setup

The next step is actually setting up your development environment. The default instructions on setting up a [Learn Development Environment ](https://github.com/AspenJames/linux-env-setup) are fairly accurate with a couple tweaks for the Pi. I recommend giving the steps below a full read before setting things up, as the order you perform a few of these definitely matters!

Follow those directions with these changes:

### Issue: Missing jvm server

If you run into an error while installing packages that you're "missing jvm server", this workaround should fix it

 First, purge and re-install openjdk:
 -  `sudo apt-get purge openjdk-8-jre-headless`
 - `sudo apt-get install openjdk-8-jre-headless`
 - `sudo apt-get install openjdk-8-jre`

Next, copy the client directory into a new server directory:
 - In your terminal, navigate to /usr/lib/jvm/java-8-openjdk-armhf/jre/lib/arm
 - Execute this command: `sudo cp -r client server`
 - Reboot your system

### Bash Login Shell

You'll have to change the default password in order to run a login shell remotely. You can do this by opening a terminal and executing `passwrd`. This will ask for your current password (default is "raspberry") and to enter a new password. Make sure you make a note of this, as you'll need to enter it to access remotely. 

I couldn't find a way for lxterminal to automatically load a login shell when opened, so you'll just have to run the command `bash -l` when opening a new terminal.** Be sure to run this command before setting up RVM and your Ruby Gems!**

### Code Editor

As far as I've been able to find, getting Atom to run on a Pi is a headache if not impossible. However, VS Code can be installed quite simply with [these directions](https://www.raspberrypi.org/forums/viewtopic.php?t=191342).

### Other programs

As far as other programs, I tried to keep things to a minimum to reduce the overall weight of the OS and programs. I kept the default Chromium browser instead of trying to install Chrome and didn't bother with Slack, Zoom, etc. Since you'll be accessing this development environment on the go, all that's really necessary is setting up RVM, git, learn, and your code editor! 

## Notes:

You'll have to have the Raspberry Pi powered on and connected to the internet in order to access it remotely. The Pi doesn't consume much power, so you could theoretically leave it plugged in when you anticipate needing access to it, however connecting it to a smart plug is another option! There are many options for plugs and outlets you can control remotely as well, so explore those options if that interests you!

VNC can be used to access any computer you have it installed on and logged in. The free account allows you to connect five devices (I believe), so in theory you could connect your phone to any computer you have a working development environment on, provided it's powered on and connected to the internet.

## Screenshots!

Here are a couple screenshots of the system as accessed by my phone. Getting used to the controls can be a bit of a learning curve, but the mouse navigation is actually quite intuitive, and the keyboard gives you access to things like Ctrl, arrow keys, etc!

![](https://i.imgur.com/CRBkMfz.png)

![](https://i.imgur.com/o9NcIi4.png)

![](https://i.imgur.com/0C2x3YY.png)


