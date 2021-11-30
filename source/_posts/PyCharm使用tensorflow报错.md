---
title: PyCharm使用tensorflow报错：libcublas.so.10.0：cannot open shared object file：No such file or directory
date: 2021-11-30 19:20:54
tags:
 - DeepLearning
 - TensorFlow
 - Error Record
categories: DeepLearning
---

# 问题描述

PyCharm使用tensorflow-gpu报错：

```
libcublas.so.10.0: cannot open shared object file: No such file or directory
```

但是在PyCharm的Teminal中可以正常使用。

<!-- more -->

# 解决方法

在Run/Debug Configurations中设置Environment，在Environment variables中加上以下环境变量：

```bash
LD_LIBRARY_PATH=/usr/local/cuda/lib64
```

