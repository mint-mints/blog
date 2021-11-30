---
title: linux中cp：omitting directory `XXX' 问题解决
date: 2021-11-19 17:31:43
tags:
 - Linux
 - Error Record
categories: Linux
---

# 问题描述

在linux系统中复制文件夹时提示如下：

```bash
cp: omitting directory `XXX' 
```

XXX是要复制的文件夹名，出现该警告的原因是因为XXX目录下**还存在文件**，所以不能直接拷贝。

<!-- more -->

# 解决办法

解决办法：使用递归拷贝，在cp命令后面加上-r参数，如：

```bash
cp -r XXX test
```

这里的 -r 代表递归的意思。

同样，当我们在linux系统下删除目录时也需要加上-r参数 ，如果目录为空，则会直接删除，如果目录非空，则会级联删除。

如删除XXX文件夹：

```bash
rm -rf XXX
```
