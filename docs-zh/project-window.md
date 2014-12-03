---
layout: docs-zh
title: 工程窗口
---

exVim默认使用[ex-project](http://github.com/exvim/ex-project)浏览工程文件。
你可以通过按下`<ctrl-Tab>`将工程窗口切换至NERDTree窗口。你也可以设置`.exvim`文件中的
`project_browser=nerdtree`将NERDTree作为你的默认的工程浏览窗口。

当你打开exVim工程时，你将会看到：

![exvim-first-start-with-text]({{site.url}}/docs/images/exvim-first-start-with-text.png)

## 构建工程浏览树

在[开始]({{site.url}}/docs/zh/getting-start)章节，我已经展示了如何使用ex-project插件构建工
程树。基本上只需要将你的光标移至工程窗口，然后按下`<leader>R`即可。
ex-project将会构建如下所示的工程树：

![ex-project-tree]({{site.url}}/docs/images/ex-project-tree.png)

### 刷新当个文件夹

有时候，你仅仅改变一个文件夹的文件，但是使用`<leader>R`将会构建整个工程，有点大才小用，这时候我们
可以将光标移至你改变了的文件夹名上，然后按下`<leader>r`，此时，它仅仅会刷新你光标下的文件夹。

### 过滤文件夹

[ex-project](http://github.com/exvim/ex-project)允许你在构建工程树时包含或者排除子目录。
exVim主要通过`.exvim`实现此功能。打开你的`your-project.exvim`, 找到`folder_filter_mode`
和`folder_filter`项.、

`fo2lder_filter_mode` 有'include'和'exclude'俩个值。 `folder_filter` 可以是以`,` 隔开的
工程子目录的文件夹名。

建议你的工程子目录是： *bin*, *src*, *tests*, *core*, *examples* 和 *docs*.
如果你希望构建的工程树里面仅仅包含src和core，你只需要将选项设置成如下：

```
folder_filter_mode = include
folder_filter += src,core
```

如果你希望构建的工程树里面包含除了*bin*和*test*之外的目录，你可以设置为：

```
folder_filter_mode = exclude
folder_filter += bin,test
```

**注意事项:**为了使你设置的选项工作，需要保存设置，然后将光标移至工程窗口，重新构建。

### 过滤文件

你可以使用`your-project.exvim`文件中提供的`file_filter` 选项。`file_filter`接受以`,`隔开
的文件名后缀。

比如，如果你只希望展示以*.lua*, *.c*, *.h*为后缀的文件，你只需要将`file_filter`设置为如下即可：

```
file_filter += lua,c,h
```

`file_filter` 也接受以`__EMPTY`命名的无后缀的文件，比如：

```
file_filter += __EMPTY__,lua,c,h
```

这将会将类似于LICENSE, README, Makefile, ... 的文件添加到你的工程树里。

**注意事项：** 为了使它工作，同样需要保存并且重新构建。

需要获取更多关于文件及文件夹过滤的信息，可以阅读[Config .exvim]({{site.url}}/docs/config-exvim).

## 文件夹的折叠

你可以将光标移至一个文件夹名所在列，通过重复按下`<Enter>`折叠和打开一个文件夹, 如下所示。

![ex-project-folding]({{site.url}}/docs/images/ex-project-folding.png)

你也可以在工程窗口使用vim内置的折叠快捷键，比如：

 - 使用 `zO` 和 `zM` 打开和折叠整个工程。
 - 使用 `zo` 和 `zc` 打开和折叠当前文件夹。
 - 使用 `zk` 和 `zj` 移至俩个折叠的中间。

## 工程窗口内光标的移动

最基本的，你可以使用`h`,`j`,`k`,`l` 和 `arrow keys`在工程窗口移动。ex-project插件也提供了
`<ctrl-k>` 和 `<ctrl-j>`俩个快捷键用于在俩个文件夹间快速移动。

你应该已经注意到了，ex-project使用 `{` 和 `}`作为它的折叠标志：

![ex-project-foldmarker]({{site.url}}/docs/images/ex-project-foldmarker.png)

这意味着你可以使用折叠跳转命令及快捷键：

 - 将你的光标移到折叠的开始或者结束处， 然后按下`%` 就可以匹配折叠
 - 使用 `[{` 和 `]}` 可以跳至上一个或者下一个折叠


## 编辑窗口的使用

### 编辑文件

当你在工程窗口的文件上按下`<enter>`时，ex-project将尝试在编辑窗口打开文件。你也可以通过按下
`<shift-enter>`将编辑窗口分割成俩个进行文件的编辑。

### 打开文件浏览器

当在工程窗口的文件下按下`<shift-enter>`时，ex-project将会使用系统自带的文件浏览器，并在里面打开
当前文件夹。这当你想在一个目录中操作一些文件时是非常有用的。

### 定位你当前的文件

如果你正在编辑一个文件，然后试图定位在工程窗口的位置，可以按下`<leader>fc`。这个操作将引起
ex-project搜索当前编辑文件，并将光标移至它。

## 创建新文件

想在工程窗口创建一个新文件，可以将光标移到一个文件或者文件夹下，然后按下`o`, ex-project将会帮你
创建一行，如下所示：

![ex-project-new-file]({{site.url}}/docs/images/ex-project-new-file.png)

输入文件名，按下`<enter>`键，将在编辑窗口打开。编辑，然后使用`:w`保存，将会创建一个新文件。

## 创建一个新文件夹

创建一个文件夹比创建文件复杂多了。首先你需要将光标移动到一个已经存在的文件夹下。这样ex-project才会
理解你要在那个文件下创建一个新文件夹。做完上面的步骤后，按下`O`(大写的o),ex-project将会要求你输入
文件夹名：

![ex-project-new-folder]({{site.url}}/docs/images/ex-project-new-folder.png)

当你输入名字并且按下enter键确认后，ex-project将会直接在选定的文件夹下创建一个新目录。

## 使用NERDTree

ex-project能够和NERDTree完美的工作。将光标移动到你的工程窗口，然后按下`<ctrl-tab>`,工程窗口将会
自动切换至NERDTree。更帅的是，`<leader>fc`依旧能够使用。切换回去的命令也是按下`ctrl-tab>`。

## .exvim 工程间的切换

你可能有许多个`.exvim`文件在你的工程里, exVim支持他们之间动态的切换, 通过打开不同`.exvim`文件，
并且通过`:w`显示保存此文件，将会切换到新的工程。

![ex-project-multiple-exvim-files]({{site.url}}/docs/images/ex-project-multiple-exvim-files.png)
