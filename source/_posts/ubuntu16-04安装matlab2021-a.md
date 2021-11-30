---
title: ubuntu16.04安装matlab2021.a
date: 2021-11-30 21:13:00
tags:
 - Linux
categories: Linux
---

# 安装步骤

使用R2021a_Linux.iso虚拟光驱进行安装

```bash
sudo mkdir/media/matlab  # 建立一个挂在目录
sudo mount -o loop R2021a_Linux.iso  /media/matlab   # 可以在/media/matlab中看到文件了
```

进入挂载目录后安装：

```bash
sudo ./insall
```

<!-- more -->

# 产品选择

毕竟MATLAB太大了，可以针对自己的专业来选择下载产品组件。

matlab官网提供了这些组件的解释： https://ww2.mathworks.cn/help/releases/R2019b/index.html ，可以按需选择。

# 快捷图标创建

输入命令：

```bash
sudo gedit /usr/share/applications/matlab.desktop   # 新建一个名为matlab.desktop的文件。
```

输入以下内容：

```bash
[Desktop Entry]
Type=Application
Name=Matlab
GenericName=Matlab 2010b
Comment=Matlab:The Language of Technical Computing
Exec=sh /usr/local/MATLAB/R2021a/bin/matlab -desktop
Icon=/usr/local/MATLAB/R2021a/toolbox/nnet/nnresource/icons/matlab.png
StartupNotify=true
Terminal=false     # 在启动matlab时不启动终端
Categories=Application;
```

其中Exec和Icon的路径需要根据自己的安装位置更改。
