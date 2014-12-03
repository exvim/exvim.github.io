---
layout: docs
title: 配置 .vimrc
---

exVim 为用户提供4种不同的 .vimrc: `.vimrc`, `.vimrc.plugins`, `.vimrc.plugins.local`,`.vimrc.local`. 

首先被载入的文件是 .vimrc，我们都熟悉它。在 .vimrc 配置你的 vim 之前，它会在同一个目录检查是否存在 `.vimrc.plugins` 然后载入它。这是 exVim 插件的默认设置。在 `.vimrc.plugins` 被运行后, `.vimrc.plugins.local` 会被载入。在它之后，`.vimrc` 才开始使用自己的设置，在最后，它会检查并载入 `.vimrc.local`

## .vimrc

`.vimrc` 的结构可以分为以下几部分：

- setup encoding
- filetype off
- load `.vimrc.plugins` if exists
  - deafult plugins settings
- load `.vimrc.plugins.local` if exists
  - install your own plugins
  - customise plugins
- filetype on
- general settings
- visual settings
- Vim UI settings
- text edit settings
- auto commands
- key mappings
- load `.vimrc.local` if exists
  - customise
  - overwrite default settings

## .vimrc.plugins

这是 exVim 插件的默认配置文件

## .vimrc.plugins.local

你可以把你自己对插件的设置放在这个文件里，也可以安装插件（在这文件里），你可能会有如下疑问：

- 我们能否放在 `.vimrc.plugins`?
- 为什么我们需要 `.vimrc.plugins.local`？
- 为什么不使用 `.vimrc.local` 来代替它？


简单来说，`.vimrc.plugins.local` 是为了防止用户覆盖掉 `.vimrc.plugins`, 并且，你可以保持 git 改变并加入自定义配置而不用担心 git 的 updates

我们默认使用 Vundle,它要求把插件管理脚本写在 filetype off 和 on 之间。这就是为什么我们使用 `.vimrc.plugins.local` 和 `.vimrc.local`. 第一个确保插件代码在 filetype off 和 on 之间。

## .vimrc.local

在 `.vimrc.local` 上你可以做很多事情，比如：

自定义你的字体:

```vim
au! ex_gui_font " 移除旧的字体设置
set guifont=Consolas:h8:cANSI " 设置你想要的字体
```

自定义你的 vim-airline 主题：

```vim
au VimEnter * exec 'AirlineTheme your_theme'
```

关闭 vim-airline:

```vim
au VimEnter * exec 'AirlineToggle' " close vim-airline plugin
```
