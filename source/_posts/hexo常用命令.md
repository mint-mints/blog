---
title: hexo常用命令
date: 2021-12-01 17:15:03
tags: Hexo
categories: blog
---

## 常用命令

```bash
npm install -g hexo-cli
npm install hexo -g #安装Hexo
npm update hexo -g #升级
hexo init #初始化博客
```

<!-- more -->

命令简写：

```bash
hexo n "我的博客" == hexo new "我的博客" #新建文章
hexo g == hexo generate #生成网页
hexo s == hexo server #启动服务预览，本地预览
hexo d == hexo deploy #部署
```

```bash
hexo server #Hexo会监视文件变动并自动更新，无须重启服务器
hexo server -s #静态模式
hexo server -p 5000 #更改端口
hexo server -i 192.168.1.1 #自定义 IP
hexo clean #清除缓存，若是网页正常情况下可以忽略这条命令
```

## 发布网站

- 在blog根目录里的_config.yml文件称为**站点**配置文件。
- 进入根目录里的themes文件夹，里面也有个_config.yml文件，这个称为**主题**配置文件。

打开**站点的配置文件_config.yml**，翻到最后修改为：

```
deploy:
	type: git
	repo: 这里填入你之前在GitHub上创建仓库的完整路径，记得加上.git
	branch: master
```

保存站点配置文件。

其实就是给**hexo d** 这个命令做相应的配置，让hexo知道你要把blog部署在哪个位置，很显然，我们部署在我们GitHub的仓库里。

最后安装Git部署插件，输入命令：

```bash
npm install hexo-deployer-git --save
```

这时，我们分别输入三条命令：

```bash
hexo clean 
hexo g 
hexo d
```

其实第三条的 hexo d 就是部署网站命令，d是deploy的缩写。完成后，打开浏览器，在地址栏输入你的放置个人网站的仓库路径，即 [http://xxxx.github.io](https://link.zhihu.com/?target=http%3A//xxxx.github.io) 就会发现你的博客已经上线了，可以在网络上被访问了。
