---
title: Tensorflow报错：OutOfRangeError：FIFOQueue '_0_input_producer' is closed and has insufficient elements
date: 2021-11-30 19:15:24
tags:
 - DeepLearning
 - TensorFlow
 - Error Record
categories: DeepLearning
---

# 问题描述

Tensorflow加载图片时报错：

```
OutOfRangeError : FIFOQueue '_0_input_producer' is closed and has insufficient elements
```

<!-- more -->

# 解决方法

因为局部变量（local variables）没有初始化，将初始化变量语句改为

```python
tf.global_variables_initializer().run(session=sess)  # 全局变量初始化
tf.local_variables_initializer().run(session=sess)   # 局部变量初始化
```
