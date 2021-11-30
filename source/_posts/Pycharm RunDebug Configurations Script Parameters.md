---
title: Pycharm Run/Debug Configurations Script Parameters 设置路径程序不识别的问题解决
date: 2021-11-30 19:43:06
tags:
 - Python
 - Error Record
categories: Python
---

# 问题描述

在Pycharm的Run/Debug Configurations中的Parameters里，设置了路径。但是运行时始终无法识别，相对路径和绝对路径都不行，都说没有该目录。

<!-- more -->

# 解决方法

表示路径的字符串两端改为**双引号！**

Parameters 里出现的文件的路径必须用双引号表示，否则程序无法识别路径。
