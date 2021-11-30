---
title: 调用TensorFlow时出现FutureWarning：Passing (type, 1) or '1type' as a synonym of type is deprecate
date: 2021-11-30 17:07:01
tags:
 - DeepLearning
 - TensorFlow
 - Error Record
categories: DeepLearning
---

# 问题描述

import tensorflow总是出现报错：

```
FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'._np_quint8 = np.dtype([("quint8", np.uint8, 1)])
```

<!-- more -->

# 解决方法

是numpy版本的问题，numpy降级就可以了。

```bash
pip show numpy                   # 查看当前numpy版本
pip install numpy==1.16.0        # 安装旧版本，会自动卸载当前版本
```
