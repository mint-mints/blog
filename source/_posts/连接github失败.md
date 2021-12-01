---
title: 连接github失败
date: 2021-12-01 17:23:39
tags: git
categories: git
---

# 连接github失败

提交或clone代码时，偶尔会出现提交失败的情况，并提示：

```bash
OpenSSL SSL_connect: SSL_ERROR_SYSCALL in connection to github.com:443
```

<!-- more -->

## 原因：

是Git的Http代理的问题，Git支持三种协议：git://、ssh:// 和 http://，本来push的时候应该走ssh隧道的，但是因为设置了http代理，所以就走了http的代理，于是就提交不了了。

## 解决方法1：

1. 这种情况偶尔出现，可能时当时的网络问题，可以换个wifi或者热点，或者，过一会再试试（如果还不行，用方法2）。

2. 既然是因为设置了http代理，那取消该设置即可。
   使用以下命令

   ```bash
   git config --global --unset http.proxy
   ```

## 解决方法2：

```bash
git config --global http.sslVerify false
```
