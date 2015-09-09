---
layout: docs_zh
title: 创建你的发布版本
---

## 为 Mac 和 Linux 创建你的发布版本

在你的电脑中创建 `~/exvim` 目录然后从github中克隆 [exvim/main](http://github.com/exvim/main) 
项目。 

```bash
# 在你的 ~/exvim/main 目录执行:
cd ~/exvim/
git clone http://github.com/exvim/main
```

进入 `~/exvim/main`

```bash
cd ~/exvim/main/
```

编辑并运行shell脚本 `dist/package.sh`，**注意：** 在你运行它之前，需要检查并确认位于
`dist/package.sh` 中的版本号

```bash
sh dist/package.sh
```

你将得到你的版本，位于 `~/exvim/build/`

## 创建 Windows 安装程序

你必须先准备下列目录并将他们拷贝到 `c:\dev\exvim\build` ，用于安装程序.

 - DejaVuSansMono
 - exvim-{{site.version}} (通过 dist/package.sh 生成的包)
 - graphviz
 - tools
 - vim74

当创建好上述目录之后，通过Inno Setup运行位于 `exvim/main/dist` 的gen-installer.iss
