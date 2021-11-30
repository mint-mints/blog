---
title: pytorch警告（UserWarning）解决
date: 2021-11-30 19:57:09
tags:
 - Error Record
 - PyTorch
 - DeepLearning
categories: DeepLearning
---

# 问题描述

pytorch训练时遇到了如下警告：

```bash
UserWarning: Argument interpolation should be of type InterpolationMode instead of int. Please, use InterpolationMode enum.
  "Argument interpolation should be of type InterpolationMode instead of int. "
```

<!-- more -->

# 解决方法

网上说是因为torchvision和pillow不兼容导致的，我的设备里torchvision=0.9.0 and pillow=8.3.1。

我把pillow降到了6.2.2，依然有warning。

于是降低torchvision版本，但是torchvision的版本号一般都是和pytorch绑定好的，我们需要不依赖torch来更改torchvison的版本，这可以通过以下指令实现。

```bash
pip3 install --no-deps torchvision==0.8.2
```

pillow和torchvision都降版本之后，就不报警告了。

参考：https://blog.csdn.net/weixin_39518984/article/details/119897453
