---
title: 更换cuda版本后Pychram中的terminal依旧显示旧版本问题
date: 2021-11-19 17:39:30
tags:
 - DeepLearning
 - Error Record
categories: DeepLearning
---

# 问题描述

更换cuda8.0版本，在系统的terminal中显示正常，输入nvcc -V后输出正常：

```bash
$ nvcc -V
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2016 NVIDIA Corporation
Built on Tue_Jan_10_13:22:03_CST_2017
Cuda compilation tools, release 8.0, V8.0.61
```

但是在pycharm的terminal中的输出还是旧版本9.0。

<!-- more -->

# 原因分析

{% asset_img 1.png pycharm config %}

查看pycharm的设置，Terminal的设置中环境变量的属性。

发现系统环境变量中的PATH中，包含/usr/local/cuda-9.0/bin

可是在更换cuda版本时，已经将.bashrc中的cuda-9.0全部改为cuda，且在系统的Terminal中测试成功。

最后找到了是在/etc/profile中，有以下两句（哦，要命）

```bash
export  PATH=/usr/local/cuda-9.0/bin:$PATH　　　　
export  LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64$LD_LIBRARY_PATH
```

# 解决方法

将/etc/profile中配置环境变量的两句直接删除了。

但是重新source更新时，报错：

```bash
X Error of failed request: BadName (named color or font does not exist)
Major opcode of failed request: 140 (RANDR)
Minor opcode of failed request: 16 (RRCreateMode)
Serial number of failed request: 35
Current serial number in output stream: 35
```

原因是/etc/profile中包含设置分辨率的两个语句

```bash
sudo xrandr --newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync
sudo xrandr --addmode VGA-1 "1920x1080_60.00"
```

在开机时就加载过两个语句，现在重新加载就重名了。

于是选择了重启 ⇒ 成功！
