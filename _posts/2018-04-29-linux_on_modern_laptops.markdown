---
layout: post
title:      "Linux on Modern Laptops"
date:       2018-04-29 20:28:29 +0000
permalink:  linux_on_modern_laptops
---


This has been a problem that I've encountered personally, and I've read a bit about others having similar issues: getting Linux to run smoothly on "modern" laptops - specifically dual-booting. For most of us, if we don't use MacOS, we're using and are familiar with Windows OS. This hasn't caused me many problems, until I got into the wonderful world of programming. 

Windows uses an entirely different and closed-source *command shell*, which is the command-line interface. The Learn platform uses a bash shell, which is standard across MacOS and Linux, as well as several other operating systems, hence the need to install and run Linux. 

I wanted to set up a dual-boot system, since I had paid for Windows 10 and still use it for other purposes such as gaming. However, when I tried to install a system alongside Windows 10, I ran into several problems. Most times, after selecting `install`, the system would hang on the loading screen. I had a hard time finding information on what was happening, running into articles about how hardware manufacturers are optimizing for the Windows operating system. 

I rececntly discovered that my system's SATA controller was set to RAID mode despite only having one SSD. Apparently RAID mode can cause a few issues with Linux systems, so I set out to change the SATA controller mode. First, I just went into my BIOS settings and switched it and... the system would not boot at all. Turns out, this is a bit more complicated when you already have a working Windows 10 install. 

Luckily, there is a very simple workaround that I found [here](https://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/). I'll outlilne the steps below, but this basically involves dropping into safe mode, then rebooting back into normal after the switch. **Important: Changing settings such as these can lead to data loss or system failure. I highly suggest you back up any data you don't want to lose and have a Windows recovery USB handy in the case your system breaks. You'll need your admin password for your Windows account to complete this.** If you do not know your admin password, you can do so by following the directions [here](https://www.top-password.com/knowledge/reset-windows-10-password.html) (I recommend method 2 for its simplicity). If you need to create a USB recovery drive, follow the steps [here](https://support.microsoft.com/en-us/help/17422/windows-8-create-usb-recovery-drive).

1. Press your Windows key (between `Fn` and `Alt` on the left of the space bar) to bring up your start menu and type "cmd". Right click the result and select "Run as Administrator". 
2. Within the command shell terminal, type `bcdedit /set {current} safeboot minimal`.  If that does not work, type `bcdedit /set safeboot minimal`.
3. Restart your computer and enter the BIOS setup. If you need more info, [click here](https://www.makeuseof.com/tag/enter-bios-computer/).
4. Change the SATA Operaton to AHCI. You may have to browse about some options to find this.
5. Save changes and exit. Windows will boot into Safe Mode. 
6. Repeat step 1 to open an elevated Command Prompt once again. 
7. Within the terminal, type `bcdedit /deletevalue {current} safeboot`. If you omitted the `{current}` in step 2, omit it here as well. 
8. Restart your computer again and you're done! 

I also had some problems specific to my system, since it has an NVIDIA graphics card and an NVMe SSD. The workaround here was to add some specific kernel boot parameters before the install. To add boot parameters, simply press `e` when you've selected `install` from your USB device instead of pressing `Enter`. This will bring you to the "GNU GRUB" menu where you can add your parameters. Find the line that starts with "linux" and add your paramters to the end of this line. I needed to add `nouveau.modeset=0` and `nvme_load=YES` to make mine work, but search for your specific system if you are still having issues. More info on kernel boot parameters can be found [here](https://wiki.ubuntu.com/Kernel/KernelBootParameters). 

Once I did the above steps, installation was a breeze! Be sure to select "Install alongside Windows" or "Something else" if you don't want to lose your Windows OS and all associated data! Once you're installed and booted up, follow [these instructions](https://github.com/learn-co-curriculum/linux-env-setup) to set up your environment. For more up-to-date instructions as of Ubuntu 18.04 LTS, follow [my fork](https://github.com/AspenJames/linux-env-setup). Happy coding!



