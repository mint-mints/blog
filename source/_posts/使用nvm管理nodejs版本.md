---
title: 使用nvm管理nodejs版本
date: 2021-12-01 17:18:36
tags:
 - nodejs
categories: nodejs
---

## 使用nvm管理nodejs版本

### 安装

要用指令升级nodejs到新版本要先安装n模块

window用不了n模块  可以用 nvm-windows : https://github.com/coreybutler/nvm-windows，下载nvm-setup.zip，安装即可。

<!-- more -->

检查是否安装成功：

```
nvm ls
```

如果你本机已经安装了nvm，那么执行这条命令时，会列出你本机安装过的所有nodejs版本。

### 切换版本

```
nvm use <版本号>
```

但是版本切换的时候要注意，从高版本切换到低版本的话有可能会有些内容不能兼容，例如，async 和 await 语句在8.14.0版本之前是不支持的。

### 安装新版本

```
nvm install <版本号>
```

去nodejs官网上查到所有的版本，进入到nodejs 官网https://nodejs.org/en/download/，可以看到版本信息。

### nvm切换镜像源

找到nvm文件夹下settings.txt，修改成下面内容(下载源)

```
root: C:\nvm
path: C:\nodejs

#新增

arch: 64 
proxy: none 
node_mirror: http://npm.taobao.org/mirrors/node/ 
npm_mirror: https://npm.taobao.org/mirrors/npm/
```

前面两行是安装的时候，自动生成的root: C:\nvm 对应你的安装位置,path: C:\nodejs 对应nodejs的位置。这两行不用改，然后保存完成。这样，就使用的淘宝的镜像下载node和npm了。
