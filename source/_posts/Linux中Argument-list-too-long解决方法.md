---
title: Linux中Argument list too long解决方法
date: 2021-11-16 16:56:24
tags: 
 - Linux
 - Error Record
categories: Linux
---

# 问题描述

Linux下使用`cp，mv，rm`等命令时经常会碰到“Argument list too long”错误，这主要是因为这些命令的参数太长，即文件个数过多。

<!-- more -->

# 解决方法

### 解决方法1：

```bash
find test/ -name "*.jpg" | xargs -i cp {} train
```

`find test/ -name "*.jpg"`是指在`test`文件夹下查找名为`*.jpg`的文件。

`xargs`命令是给其他命令传递参数的一个过滤器，也是组合多个命令的一个工具。`-i`会将`xargs`的内容赋值给`{}`。

### 解决方法2：

```bash
find test/ -name "*.jpg" -exec cp {} train \\;
```

`-exec`参数后面是指执行其后面的命令，`-exec`以`;`为结尾，由于各个系统中分号的意义不同，因此用`\\`进行转义，即`\\;`，`{}`会被`find`find命令的结果替换。
