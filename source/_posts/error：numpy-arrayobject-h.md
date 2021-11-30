---
title: fatal error：numpy/arrayobject.h：No such file or directory compilation terminated.
date: 2021-11-30 19:17:33
tags:
 - DeepLearning
 - Error Record
categories: DeepLearning
---

# 问题描述

复现论文代码时报错：

```
fatal error: numpy/arrayobject.h: No such file or directory compilation terminated.
```

<!-- more -->

# 解决方法

其实numpy已经是安装的，anaconda里面有，python中import numpy也没有问题，但就是在此处报错。

执行以下命令，就可以了。

```bash
sudo apt-get install python-numpy
```
