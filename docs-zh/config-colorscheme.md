---
layout: "docs-zh"
title: 配色配置
published: true
---

exVim 的配色由三部分组成: 你自己的Vim配色, exVim 插件的语法高亮和插件的配色. 你可以按照以下步骤来定制你的配色:

## 安装你的配色

exVim 提供了三种方法安装你的自定义配色

**方法1. 在 ex-colorscheme 中安装（推荐）**

首选的方法是在 [ex-colorschemes](https://github.com/exvim/ex-colorschemes) 中安装自己的配色, 这种方法仅仅需要你把自己的配色文件放到 `vimfiles/bundle/ex-colorschemes/colors/` 文件夹中. 请先确认你已经在 `.vimrc.plugins` 中有安装了 [ex-colorschemes](https://github.com/exvim/ex-colorschemes) 插件

**方法2. 在 Vim 颜色文件中安装**

如果你不喜欢安装 ex-colorscheme 插件, 你可以像安装 Vim 插件一样安装配色. 即将你的配色文件放在 vimfiles/colors 文件夹中.

**方法3. 通过 Vim 插件 Vundle 安装**

方法2 不遵循 Vim 的插件管理结构. 所以我们可以使用 Vundle 或者 Pathogen 来安装我们自己的配色. 和 [ex-colorschemes](https://github.com/exvim/ex-colorschemes) 一样, 安装你自己的插件, 把你的配色文件脚本放在里面然后上传至 Github, 然后再在 `.vimrc.plugins.local` 中用Vundle 安装

## 配置 exVim 插件语法高亮

exVim 使用 [ex-aftercolor](https://github.com/exvim/ex-aftercolors) 插件来动态更新配色. ex-aftercolor 会在配色改变运行定义在其内部的配色代码, 从而实现动态改变配色的功能.

[ex-aftercolor](https://github.com/exvim/ex-aftercolors) 会触发运行路径中 `after/` 文件夹的颜色脚本. 详细内容请参考 [ex-aftercolor](https://github.com/exvim/ex-aftercolors) 项目.

exVim 把它自定义的脚本放在 `vimfiles/bundle/ex-config/after/colors/` 文件夹中, 默认情况下, 他支持 [solarized](https://github.com/altercation/vim-colors-solarized) 和 ex-lightgray 两种配色的动态改变.


为了自定义你自己的配色, 你必须创建一个和你的配色文件一样名字的文件在 `after/colors` 文件夹下. 你可以选择放在如下几个地方:

1. vimfiles/bundle/ex-config/after/colors/ （如果你选择方法1建议选择这个）
1. vimfiles/bundle/ex-colorschemes/after/colors/ （如果你选择方法1建议选择这个）
1. vimfiles/after/colors/ （如果你选择方法2建议选择这个）
1. your_own_color_bundle/after/colors/ （如果你选择方法3建议选择这个）

一旦你确定了放置位置并且创建了文件, 那么你可以参考 `vimfiles/bundle/ex-config/after/colors/solarized.vim` 或者
 `vimfiles/bundle/ex-config/after/colors/exlightgray.vim`, 沿用他们的代码来配置你自己的颜色.

如下是一个在 aftercolor 脚本中你可以配置的语法高亮清单：

| Name | Usage or reference |
| :---- | :---- |
| exConfirmLine | Color of selected line in ex-gsearch, ex-symbol, ... window |
| exTargetLine | Color of selected line in edit window |
| ex-showmakrs Highlighting | Check `:help showmarks-highlighting` |
| ex-easyhl Highlighting | Check `:help easyhl-highlighting` |
| ex-project Highlighting | Check `:help exproject-highlighting` |
| ex-gsearch Highlighting | Check `:help exgsearch-highlighting` |
| ex-symbol Highlighting | Check `:help exsymbol-highlighting` |