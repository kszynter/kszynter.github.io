---
layout: post
title:  "resetting root password using GRUB"
date:   2017-07-22 12:11:17 +0200
categories: linux password rescue grub vm virtualbox yak
---
TL;DR
=

reboot machine, enter GRUB, 'e', add 'init=/bin/bash', 'F10', 'mount -rw -o remount /', passwd

Long story
=

If you find yourself in a situation where you forgot even a login name to your old linux machine, you can reset the root password if you have acceess to the GRUB when the machine boots up:
1. when the GRUB menu shows up, use keyboard arrows to stop the timeout that will boot the machine in few seconds
2. press 'e' on a keyboard to enter edit mode and find the line specyfing a kernel 'linux /vmlinuz-...'
3. at the end of this line add (with a leading space) 'init=/bin/bash'
4. press F10 key to boot with using just edited configuration
5. when in terminal remount root partition with write access using this command 'mount -rw -o remount /'
6. now reset your password with a command 'passwd'
7. reboot the machine, preferably with 'reboot' command but it may show the error so.. just kick it manually if there is no other way

