---
title: conda安装tensorflow报错：PackagesNotFoundError
date: 2021-11-16 17:11:14
tags: 
 - DeepLearning 
 - TensorFlow
 - Error Record
categories: DeepLearning
---

# 问题描述

conda安装tensorflow报错：PackagesNotFoundError: The following packages are not available from current channels。

<!-- more -->

```bash
conda install ‐‐channel https://conda.anaconda.org/anaconda tensorflow‐gpu=1.9.0
Collecting package metadata (current_repodata.json): done
Solving environment: failed with current_repodata.json, will retry with next repodata source.
Collecting package metadata (repodata.json): done
Solving environment: failed
PackagesNotFoundError: The following packages are not available from current channels:

  - tensorflow‐gpu=1.1.0
  - ‐‐channel
  - //conda.anaconda.org/anaconda

Current channels:
  - https://repo.anaconda.com/pkgs/main/linux-64
  - https://repo.anaconda.com/pkgs/main/noarch
  - https://repo.anaconda.com/pkgs/r/linux-64
  - https://repo.anaconda.com/pkgs/r/noarch

To search for alternate channels that may provide the conda package you're looking for, navigate to   https://anaconda.org  and use the search bar at the top of the page.
```



# 解决方法

更换为pip安装

```bash
pip install tensorflow-gpu==1.1.0
```
