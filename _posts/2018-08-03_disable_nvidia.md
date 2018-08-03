---
layout: post
title: Disable nvidia card while installing Ubuntu 16.04
data: 2018-06-18 10:57:00
---
# Disable nvidia card while installing Ubuntu 16.04
> This usually happens on a laptop <br/>

You can read this [answer](https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics) to have an overview
1. Reboot into GRUB.
2. Highlight the Ubuntu option and press E.
3. Add nouveau.modeset=0 to the end of the line beginning with linux.
4. Press F10 to boot.
