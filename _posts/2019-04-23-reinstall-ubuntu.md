---
tags: IT
title: Re-Install Ubuntu after it was down
excerpt: Easy and no harm
comments: true
---

![cc](/public/cc.png) Also published on [S&C](https://soandcandy.us)

My Ubuntu 18.04 LTS ran for a long time, and I did many things what maybe slow down the computer, what was worse, it could NOT boot normally as usual. When I checked the log file, found that it due to some error of the Elan touchscreen. May be some error of the EFI file, too.

So, I decided to re-install a new one. 

As you know, I had Ubuntu and Windows 10 dual boot systems. 

- I login to Windows 10 to do the backup job.
- Under the Windows 10, RUN **PowerShell**, with administrator.
- Input `diskmgmt.msc`, WIPE the Ubuntu system partition. Mega them to one partition.
- Use Etcher to flash your Ubuntu 18.04 LTS, or other systems you want, to an USB disk.
- Insert the USB disk and boot to BIOS.
- Disable the secure boot, and choose USB driver first boot.
- There you go. Install the Ubuntu as normal. 

**REMEMBER to choose Install alongside the Windows boot manager**

It is better for beginners, in my opinion.


#### BACKUP YOUR FILES FIRST! ####



![so](/public/favicon.ico)


