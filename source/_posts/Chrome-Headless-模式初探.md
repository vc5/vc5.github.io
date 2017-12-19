---
title: Chrome-Headless-模式初探
date: 2017-11-11 18:50:12
tags:
---

##  遇到的坑
###  树莓派启动chrome报错
`[1111/185140.971519:ERROR:browser_main_loop.cc(582)] Failed to put Xlib into threaded mode.`
#### 产生原因
因为没有进入图形界面，$DISPLAY没有被正确设置[参见](https://github.com/RPi-Distro/repo/issues/58)
#### 解决办法
chromium启动前运行DISPLAY=:0[参见](https://www.raspberrypi.org/forums/viewtopic.php?t=176129)
