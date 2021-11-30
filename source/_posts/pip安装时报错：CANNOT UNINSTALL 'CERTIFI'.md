---
title: pip安装时报错：CANNOT UNINSTALL 'CERTIFI'. IT IS A DISTUTILS INSTALLED PROJECT
date: 2021-11-30 19:52:18
tags:
 - Python
 - Error Record
categories: Python
---

# 问题描述

使用pip进行安装时报错：

{%asset_img 1.png %}

```
Cannot uninstall 'certifi'. It is a distutils installed project and thus we cannot accurately determine which files belong to it which would lead to only a partial uninstall.
```

<!-- more -->

# 解决方法

{%asset_img 2.png %}

修改pip版本后重新安装，安装成功。

但是会给出警告：

{%asset_img 3.png %}
