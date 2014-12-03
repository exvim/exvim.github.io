---
layout: docs-zh
title: 配色配置
---

exVim的配色由三部分组成：你自己的Vim配色；exVim插件的语法高亮和插件的配色。如果要自定义你的配色，
你必须遵循以下步骤：

## 安装你的配色

在exVim中有三个地方可以安装你自己的配色

方法1.在ex-colorscheme中安装（推荐）

[ex-colorschemes](https://github.com/exvim/ex-colorschemes) plugins in your `.vimrc.plugins`.
推荐你在ex-colorscheme中安装自己配色，（这种方法）仅仅需要你把自己的配色文件放到`vimfiles/bundle/
 ex-colorschemes/colors/`中。确保在.vimrc.plugins中有安装[ex-colorschemes](https://github.com/
 exvim/ex-colorschemes)插件

方法2.在Vim颜色文件中安装

如果你不喜欢安装ex-colorscheme插件，你可以像安装VIM插件一样安装配色。即将你的配色文件放在
vimfiles/colors文件夹中。

方法3.通过vim插件bundle安装

方法2不遵循vim的插件管理结构。所以我们可以使用vundle或者Pathogen来安装我们自己的配色。

像[ex-colorschemes](https://github.com/exvim/ex-colorschemes)一样安装你自己的插件，把你的配色文件
脚本放在里面然后上传至Github,然后再在.vimrc.plugins.local中用Vundle安装

## 配置exVim插件语法高亮

exVim使用[ex-aftercolor](https://github.com/exvim/ex-aftercolors)插件在配色改变后来管理语法高亮。
[ex-aftercolor](https://github.com/exvim/ex-aftercolors)会触发运行路径中after/文件夹的颜色脚本。详细
内容参考[ex-aftercolor](https://github.com/exvim/ex-aftercolors)

exVim把它自定义的脚本放在`vimfiles/bundle/ex-config/after/colors/`文件夹中，默认情况下，他支持
[solarized](https://github.com/altercation/vim-colors-solarized)和exlightgray.


为了自定义你自己的配色，你必须创建一个和after/colors文件夹下配色一样名字的文件。你可以放在如下
三个地方：

1. vimfiles/bundle/ex-config/after/colors/ （如果你选择方法1建议选择这个）
1. vimfiles/bundle/ex-colorschemes/after/colors/ （如果你选择方法1建议选择这个）
1. vimfiles/after/colors/ （如果你选择方法2建议选择这个）
1. your_own_color_bundle/after/colors/ （如果你选择方法3建议选择这个）

一旦你选择了位置并且创建了文件，像`vimfiles/bundle/ex-config/after/colors/solarized.vim` 或者
 `vimfiles/bundle/ex-config/after/colors/exlightgray.vim`一样来配置你自己的配色


如下是一个在aftercolor脚本中你可以配置的语法高亮清单：

| Name | Usage or reference |
| :---- | :---- |
| exConfirmLine | Color of selected line in ex-gsearch, ex-symbol, ... window |
| exTargetLine | Color of selected line in edit window |
| ex-showmakrs Highlighting | Check `:help showmarks-highlighting` |
| ex-easyhl Highlighting | Check `:help easyhl-highlighting` |
| ex-project Highlighting | Check `:help exproject-highlighting` |
| ex-gsearch Highlighting | Check `:help exgsearch-highlighting` |
| ex-symbol Highlighting | Check `:help exsymbol-highlighting` |

