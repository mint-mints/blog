---
title: TypeError：'module' object is not callable 报错解决
date: 2021-11-30 20:05:04
tags:
 - Error Record
 - Python
categories: Python
---

# 问题描述

```bash
# 定义
class A:
     #constructor
     def __init__(self):
          xxx
     def run(self):
          return something

# 调用
>>> import A
>>> a = A()
>>> a.run()
# 报错
Traceback (most recent call last):
  File "..../main.py", line 5, in <module>
    a = A()
TypeError: 'module' object is not callable
```

<!-- more -->

# 解决方法

Python导入模块的方法有两种：import module 和 from module import，区别是前者所有导入的东西使用时需加上模块名的限定，而后者不要。

正确的代码：

```bash
>>> import A
>>> a = A.A()
>>> a.run()
或
>>> from A import *
>>> a = A()
>>> a.run()
```
