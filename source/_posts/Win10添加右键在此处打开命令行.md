---
title: Win10添加右键在此处打开命令行
date: 2021-12-01 17:20:19
tags:
 - win10
categories: win10
---

win10通过添加注册表项，实现右击**“在此处打开命令行功能”**

### 自动导入

一键自动导入设置。将以下内容保存成reg文件，如a.reg，双击该文件自动导入设置。

<!-- more -->

```
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\Background\shell\Open CMD Here]
"ShowBasedOnVelocityId"=dword:00639bc8

[HKEY_CLASSES_ROOT\Directory\Background\shell\Open CMD Here\command]
@="cmd.exe /s /k pushd \"%V\""
```

