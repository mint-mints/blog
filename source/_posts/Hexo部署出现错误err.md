---
title: Hexo部署出现错误err：Error：Spawn failed解决方法
date: 2021-11-30 19:45:37
tags:
 - Hexo
 - Error Record
categories: blog
---

# 问题描述

Hexo部署过程中可能会出现错误

```bash
fatal: unable to access '<http://github.com/mint-mints/blog.git/>': OpenSSL SSL_read: Connection was reset, errno 10054 
FATAL {                                                                                                                  
	err: Error: Spawn failed                                                                                                   
		at ChildProcess.<anonymous> (E:\\Docs\\Blog\\blog\\node_modules\\hexo-util\\lib\\spawn.js:51:21)                              
		at ChildProcess.emit (events.js:400:28)                                                                                
		at ChildProcess.cp.emit (E:\\Docs\\Blog\\blog\\node_modules\\cross-spawn\\lib\\enoent.js:34:29)                               
		at Process.ChildProcess._handle.onexit (internal/child_process.js:277:12) {                                          
	code: 128                                                                                                            
	}                                                                                                                    
} Something's wrong. Maybe you can find the solution here: %s <https://hexo.io/docs/troubleshooting.html>
```

<!-- more -->

# 解决方法

有可能是你的git repo配置地址不正确,可以将http方式变更为ssh方式

```bash
# 修改
# Deployment
## Docs: <https://hexo.io/docs/one-command-deployment>
deploy:
  type: git
  repository: <https://github.com/mint-mints/blog.git> => git@github.com:mint-mints/blog.git  #你的仓库地址
  branch: master
```

然后重新生成页面并部署就可以

```bash
hexo clean && hexo g && hexo d
```
