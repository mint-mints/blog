---
title: ImportError：libcublas.so.8.0：cannot open shared object file
date: 2021-11-19 17:18:43
tags: 
 - DeepLearning
 - Error Record
categories: DeepLearning
---

# 问题描述

报错如下：

```
ImportError: libcublas.so.8.0: cannot open shared object file: No such file or directory
```

<!-- more -->

# 原因分析

tensorflow和已安装的cuda版本不匹配

# 解决方法

## 1. 查看已安装cuda版本

有三种方法可以查看：

（1）输入命令查看版本信息

```bash
nvcc -V
```

（2）输命令查看

```bash
ll /usr/local/cuda*
```

（3）进入/usr/local/cuda文件夹下打开version.txt，查看版本信息。

## 2. 查看cuda和tensorflow的版本对应关系

官网上有对应的说明：https://tensorflow.google.cn/install/source#linux

## 3. 安装并切换对应版本的cuda
