---
title: ubuntu切换cuda版本但nvcc显示不正确的解决办法
date: 2021-11-19 17:29:14
tags:
 - DeepLearning
 - Linux
 - Error Record
categories: DeepLearning
---

1. 在~/.bashrc 中修改好如下内容：

```bash
export PATH="$PATH:/usr/local/cuda/bin"
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64"
export LIBRARY_PATH="$LIBRARY_PATH:/usr/local/cuda/lib64
```

<!-- more -->

并且完成软链接切换

```bash
rm -rf /usr/local/cuda      #删除之前创建的软链接
sudo ln -s /usr/local/cuda-8.0 /usr/local/cuda
```

2. 加载更新后的配置

```bash
sudo -s
source ~/.bashrc
```

注：此处直接使用source后，未成功更新。若使用sudo source ~/.bashrc会报错：sudo: source: command not found

3. 使用nvcc -V查看版本，仍不起效

   使用which nvcc，出现 /usr/local/cuda-9.0/bin/nvcc

4. 果断在.bashrc中增加nvcc的环境目录

```bash
export PATH="$PATH:/usr/local/cuda/bin/nvcc"
```

5. 再次source更新，搞定！
