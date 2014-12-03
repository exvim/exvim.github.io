---
layout: docs
title: 插件 
---

用Vim工作了几年后，exVim团队在选择插件上有了一个很好的尝试。我们从vim社区里仔细的选择插件，同时
我们也开发自己的插件。对于那些作者已经停止更新的插件，我们fork下来然后修改使得他与exVim兼容。


这篇文章会告诉你exVim默认使用了哪些插件，我也建议你阅读[在vim社区里查找插件]({{site.url}}/docs/select-your-plugin)
，因为它会教你如何在vim社区里里搜索插件。

## 概述

### 插件管理 

- [Vundle](https://github.com/gmarik/vundle)
- [Pathogen](https://github.com/tpope/vim-pathogen)
- [NeoBundle](https://github.com/Shougo/neobundle.vim)
- [Vimball](http://www.vim.org/scripts/script.php?script_id=1502)

Vundle需要你在`.vimrc`中指定插件的地址，然后用命令`:PluginInstall`安装插件，在运行命令后，
Vundle会检查插件然后用Git下载最新版（意味着你电脑也必须装有Git并且主程序在path下）。你也
不运行命令:`PluginInstall`而自己下载插件，这样的话，你就像pathogen一样管理插件

Pathogen比Vundle要早出现，在管理插件上它也非常NICE。Pathogen需要你自己下载插件到指定目录。下
载完后，你只需要在`.vimrc`中添加一条简单的脚本来使它加载插件。

我不使用NeoBundle所以不介绍关于它的。

Vimball是最老的插件管理插件。它并如上面几个插件那样出色。我是为了不让vim新手不过多的关注这个
插件而介绍他的，他的文件由`*.vba`构成。

我的选择

Vundle和Pathogen都是非常好的作品。对于Vundle，你需要在‘.vimrc’中写更多的脚本来指定你想安装的
插件，然后剩下的事情它自己处理；对于Pathogen,你仅仅需要在`.vimrc`中添加一行，但是你得为每个插件
自己运行Git或者zip文件。在exVim中我选择Vundle插件但是提供pathogen支持。

这是一些讨论这些的文章：

- http://jameslaicreative.com/moving-up-upgrading-from-pathogen-to-vundle/
- http://rmitc.org/2013/04/modern-vim-plugin-management-pathogen-vs-vundle/
- http://ryanpcarney.com/technologblog/goodbye-pathogen-hello-neobundle

### 状态栏

- [vim-airline](https://github.com/bling/vim-airline)
- [powerline](https://github.com/Lokaltog/powerline)
- [MiniBufExpl](https://github.com/techlivezheng/vim-plugin-minibufexpl)

上面每一个插件都能使你的Vim状态栏更漂亮。Powerline需要python支持。vim-airline是则不需要

MiniBufExpl是一个像标签一样展示打开的每个文件的一个较老的插件。它已经停止更新很多年了
我列出的一个是Techlivezheng forked的版本。他修复了一些BUG并使它更好用。

我的选择

自从vim-airline仅用vim脚本编写后，他在exVim的插件中就不可缺少了

### 快速打开文件、缓存、MRU

- [ctrlp](https://github.com/kien/ctrlp.vim)
- [unite](https://github.com/Shougo/unite.vim)

我仅仅使用过ctrlp，它工作的非常好。所以我选择ctrlp. unite看起来不错，它的作者说unite是一
个与ctrlp有不同特性的插件

### Git操作

- [vim-fugitive](https://github.com/tpope/vim-fugitive)
- [vim-gitgutter](https://github.com/airblade/vim-gitgutter)
- [vim-gist](https://github.com/mattn/gist-vim)

vim-fugitive是一个和git配合的非常好的插件。他用命令帮你完成git托管，diff或者其他任务

vim-gitgutter会把你git文件和正在编辑的文件进行比较并且实时展示他们的不同，我非常喜欢这个idea但是
很少用到这个功能。在vim-fugitive中我用`:Ddiff`来实现这个功能。我把这个功能做成了一个选项而不是直
接集成。

vim-gist是一个上传或者block到Git的插件。

### 撤销管理

- [undotree](https://github.com/mbbill/undotree)
- [gundo](https://github.com/sjl/gundo.vim)

他们都在能在窗口中展示vim撤销记录。

我的选择

undotree更好用。当你编辑文件时他实时更新，在代码结构和BUG上也更好。

### 文件浏览

- [NERDTree](https://github.com/scrooloose/nerdtree)
- [ex-project](https://github.com/exvim/ex-project)

NERDTREE在vim中是一个真正的文件浏览器。它像一个本地文件浏览器一样浏览文件盒文件夹，它也提供
设置你不想显示的文件的选项

ex-project是一个仅仅关注exVim工程窗口的插件。他从`.exvim`文件中读取文件过滤设置，然后创建工程
文件列表

我的选择

他们两个在exVim中都工作的很好。我使用NERDTRree来编辑不在工程中的文件。但对于工程文件，ex-project
工作的更好，它可以在插件窗口中直接创建文件和文件夹，并且提供设置希望显示和隐藏文件的选项

### 当前文件的标签预览

- [tagbar](https://github.com/majutsushi/tagbar)
- [taglist](http://www.vim.org/scripts/script.php?script_id=273)

TODO

### 注释

- [NERDCommenter](https://github.com/scrooloose/nerdcommenter)
- [vim-commentary](https://github.com/tpope/vim-commentary)
- [tcomment](https://github.com/tomtom/tcomment_vim)
- [EnhCommentify](http://www.vim.org/scripts/script.php?script_id=23)

NERDCommenter不需要filetype，它工作的更好

### 代码自动补全

- [neocomplcache](https://github.com/Shougo/neocomplcache.vim)
- [neocomplete](https://github.com/Shougo/neocomplete.vim)
- [YouCompleteMe](https://github.com/Valloric/YouCompleteMe)
- [vim-autocomplpop](https://bitbucket.org/ns9tks/vim-autocomplpop/)
- [supertab](https://github.com/ervandew/supertab)

neocomplete是neocomplcache的一个新版本，但是它需要vim已+lua选项编译。它提供更快的函数补全，但
是它不是纯粹的vim脚本，许多人选择neocomplcache

Youcompleteme看起来不错，它自己介绍说是vim中最快的自动补全插件。但是它也不是纯粹的vim脚本

vim-autocomplpop 是一个很老的vim插件。很遗憾作者没有把它放在Git.所以我做了fork版本
[fork version](https://github.com/exvim/ex-autocomplpop)

我的选择

我发现在某些情况下neocomplcache工作的很慢。所以我还是使用vim-autocomplpop

### 代码片段

- [neosnippet](https://github.com/Shougo/neosnippet.vim)
- [snipmate](https://github.com/msanders/snipmate.vim)
- [ultisnips](https://github.com/SirVer/ultisnips)

没有测试他们。

一些不错的提供代码片段插件的仓库：

- https://github.com/spf13/snipmate-snippets
- https://github.com/scrooloose/snipmate-snippets
- https://github.com/honza/vim-snippets

### 语法检查

- [syntasic](https://github.com/scrooloose/syntastic)

Syntasic是一个非常好的插件，它使用你当前语言的lint来检查你的代码

### 编码检测

- [AutoFenc](https://github.com/s3rvac/AutoFenc)
- [FencView](https://github.com/mbbill/fencview)

Autofenc有多种方法来配置编码

FencView mainly supports detection of encodings for asian languages.
Fencview主要提供ASIAM语言的编码检测

### 更好的文本编辑 

- [vim-easymotion](https://github.com/Lokaltog/vim-easymotion)
- [vim-surround](https://github.com/tpope/vim-surround)
- [tabular](https://github.com/tpope/vim-surround)
- [showmarks](https://github.com/exvim/ex-showmarks)
- [visincr](https://github.com/exvim/ex-visincr)
- [matchit](https://github.com/exvim/ex-matchit)
- [LargeFile](https://github.com/vim-scripts/LargeFile)

vim-easymotion是一个vim鼠标移动命令`b`,`f`,`e`,`t`的强大增强插件

vim-surround帮助你更加简单的添加 `(`,`{`,`[`,`"`,```,..符号

tabular是一个帮你用像`=`,`,`这种符号来对齐一些文本的插件。当你在编写json或者有许多变量的代码
时非常有用

showmarks帮助你显示vim中的书签标记

visincr帮助你按顺序填写数字，在编写代码时非常有用

matchit增强vim的`%`操作

Largefile允许你使用简单的规则打开较大的vim文件

## 网页开发

### HTML

- [emmet-vim](https://github.com/mattn/emmet-vim)
- [vim-indent-guides](https://github.com/nathanaelkane/vim-indent-guides)

emmet-vim是一个强大的html辅助编写插件

vim-indent-guides能显示你文件的标签。我仅仅在编写html时才用这个插件，所以我把它列在这儿

### JavaScript, CoffeeScript, ...

- [vim-javascript](https://github.com/pangloss/vim-javascript)
- [vim-jsbeautify](https://github.com/maksimr/vim-jsbeautify)
- [vim-coffee-script](https://github.com/kchmck/vim-coffee-script)

vim-javascript包括在编写javascript时的缩进，语法高亮功能

vim-jsbeautify包括html,css,javascript缩进和语法高亮功能。我没用它所以没有建议

vim-coffee-script includes the indent, syntax highlight for editing CoffeeScript.

vim-coffee-script包括了Coffeescript的缩进，语法高亮

### JSON

- [vim-json](https://github.com/elzr/vim-json)

vim-json provides indent, syntax highlight for editing JSON file.
vim-json提供了编写JSON文件时的缩进，语法高亮

### Markdown

- [vim-markdown by plasticboy](https://github.com/plasticboy/vim-markdown)
- [vim-markdown by tpope](https://github.com/tpope/vim-markdown)

他们都很好的支持markdown的缩进，语法高亮和文件类型检测

我的选择

我使用vim-markdown,没其他原因，github粉

### CSS

- [vim-less](https://github.com/groenewege/vim-less)
- [vim-css-color](https://github.com/skammer/vim-css-color)

vim-less提供LESS的语法高亮

vim-css-color会用相对应的颜色来显示CSS颜色属性值，但是在编辑大CSS文件时比较慢

## C-lang Developer

### CRef

- [cref](https://github.com/exvim/ex-cref)

C函数的辅助插件

## Lua Developer

- [lua inspector](https://github.com/xolox/vim-lua-inspect)
- [lua-ftplugin](https://github.com/xolox/vim-lua-ftplugin)

## Go Developer

### Syntax highlight

- [go-lang](http://go-lang.cat-v.org/text-editors/vim/)
