---
title: ubuntu16.04切换cuda版本
date: 2021-11-30 21:22:51
tags:
 - Linux
categories: Linux
---

# 安装并切换为cuda8.0（5.1）

1. 实现多版本CUDA共存的第一步，就是要将先前添加到***.bashrc文件***里的环境变量路径全部指向cuda软链接，也就是环境变量的路径里所有cuda-x.0的名字都改成cuda，如下：

```bash
# Tensorflow官方安装历程要求注意的是:配置PATH和LD_LIBRARY_PATH和CUDA_HOME环境变量.
 
sudo gedit ~/.bashrc #修改配置文件（如果你用的是zsh，则需要修改 ~/.zshrc文件）
 
#在文件结尾处添加或修改以前的路径
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib64
export PATH=$PATH:/usr/local/cuda/bin
export CUDA_HOME=$CUDA_HOME:/usr/local/cuda修改后要使用sour
```

<!-- more -->

2. 在官网下载cuda安装包：https://developer.nvidia.com/cuda-toolkit-archive

   注意下载runfile类型。此处下载CUDA Toolkit 8.0 GA2版本

3. 安装

   安装过程中需要注意，不要选择安装驱动且不要生成软链接

```bash
sudo sh cuda_8.0.61_375.26_linux.run # 开始安装
 
# ..一堆协议说明...
# 直接按q退出协议说明.
Important Notice
Do you accept the previously read EULA?
accept/decline/quit: accept   # 接受协议

Install NVIDIA Accelerated Graphics Driver for Linux-x86_64 375.26?
(y)es/(n)o/(q)uit: n     # 是否显卡驱动包，由于已经安装显卡驱动，选择n

Install the CUDA 8.0 Toolkit?
(y)es/(n)o/(q)uit: y     # 是否安装工具包，选择y

Enter Toolkit Location
 [ default is /usr/local/cuda-8.0 ]:   # 工具包安装地址，默认回车即可

Do you want to install a symbolic link at /usr/local/cuda?
(y)es/(n)o/(q)uit: n     # 不添加链接**注意这个连接，如果你之前安装过另一个版本的cuda，除非你确定想要用这个新版本的cuda，否则这里就建议选no，因为指定该链接后会将cuda指向这个新的版本**

Install the CUDA 8.0 Samples?
(y)es/(n)o/(q)uit: y     # 安装样例

Enter CUDA Samples Location
 [ default is /home/nercms ]:   # 样例安装地址默认即可

# ***安装信息***
Installing the CUDA Toolkit in /usr/local/cuda-8.0 ...
Installing the CUDA Samples in /home/nercms ...
Copying samples to /home/nercms/NVIDIA_CUDA-8.0_Samples now...
Finished copying samples.

===========
= Summary =
===========

Driver:   Not Selected
Toolkit:  Installed in /usr/local/cuda-8.0
Samples:  Installed in /home/nercms

Please make sure that
 -   PATH includes /usr/local/cuda-8.0/bin
 -   LD_LIBRARY_PATH includes /usr/local/cuda-8.0/lib64, or, add /usr/local/cuda-8.0/lib64 to /etc/ld.so.conf and run ldconfig as root

To uninstall the CUDA Toolkit, run the uninstall script in /usr/local/cuda-8.0/bin

Please see CUDA_Installation_Guide_Linux.pdf in /usr/local/cuda-8.0/doc/pdf for detailed information on setting up CUDA.

***WARNING: Incomplete installation! This installation did not install the CUDA Driver. A driver of version at least 361.00 is required for CUDA 8.0 functionality to work.
To install the driver using this installer, run the following command, replacing <CudaInstaller> with the name of this run file:
    sudo <CudaInstaller>.run -silent -driver

Logfile is /tmp/cuda_install_26035.log
# ***安装完成***1
```

4. 切换cuda版本

```bash
sudo rm -rf /usr/local/cuda  #删除之前生成的软链接
sudo ln -s /usr/local/cuda-8.0 /usr/local/cuda #生成新的软链接
```

5. cuDNN安装

   在官网下载cuDNN5.1：https://developer.nvidia.com/rdp/cudnn-archive。注意下载cuda版本对应的包。

   下载完成后，进入相应的目录，解压文件。

   然后将库文件和头文件copy到cuda目录。**注意sudo cp的时候写到真实的cuda-8.0这样的路径下，不要写到cuda软链接路径，这样不影响版本对应。**

```bash
sudo cp cuda/include/cudnn.h /usr/local/cuda-8.0/include
sudo cp cuda/lib64/libcudnn* /usr/local/cuda-8.0/lib64
sudo chmod a+r /usr/local/cuda-8.0/include/cudnn.h /usr/local/cuda-8.0/lib64/libcudnn*
```

完成之后即可看到nvcc -V输出的cuda版本已经变成了10.0。再想切回cuda-9.0只需要再用上述指令给9.0的路径生成新的同名软链接即可。

PS：由于改变了cuda版本，原先安装的某些包可能出现不兼容，需要卸载重装。

