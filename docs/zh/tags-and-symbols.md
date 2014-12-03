---
layout: docs
title: 标记与符号
---

Vim的标记系统对于我们是非常有用的。使用强大ctags工具，我们能够在vim中分析
代码生成tags标记。

exVim通过采用 [ex-tags](http://github.com/exvim/ex-tags) 和 [ex-symbol](http://github.com/exvim/ex-symbol) 
插件进行改善。exVim通过`:Update`命令生成tags。

## 选择标记

在vim中可以使用`<ctrl-]`和`:ts tag-name`跳转到对应tags。[ex-tags](http://github.com/exvim/ex-tags)
提供同样的办法但是却不同的命令---`<leader>]` 和`:TS tag-name`。

你可以认为他们是原版的装饰版。

例如，假设我们想列出dlmalloc的定义与声明，我们输入`:ts dlmalloc`，vim将会
给我们展示如下内容：

![ex-tags-ts]({{site.url}}/docs/images/ex-tags-ts.png)

然后，我们可以输入对应的编号选择，或者输入`<Esc>`取消它。

在[ex-tags](http://github.com/exvim/ex-tags) ，我们输入 `:TS dlmalloc` ，然后Vim 将会展示:

![ex-tags-ts2]({{site.url}}/docs/images/ex-tags-ts2.png)

这时，你可以向上或向下移动光标，并通过'<Enter>'选择。

## 符号

符号是标记的集合。通过exVim的`:Update`命令，再通过ctags生成tags文件后，它将会读
tags，提取tag进入符号文件。这个符号文件被 [ex-symbol](http://github.com/exvim/ex-symbol)
用于快速的搜索。

当你忘记精确的tags单词时，符号将会非常有用，它将会帮助你在tags名称表中搜索，并允许
你通过类似于[Global Search]({{site.url}}/docs/global-search)的过滤方法过滤结果。

### 符号列表

ex-symbols 提供四个不同的办法在符号窗口列举tags：

| 命令                    | 用途                                                                                                                      |
| :--------------- ------| :--------------------------------------------------------------------------------------------------- |
| `<leader>ss`       | 列举所有的symbols                                                                                             |
| `<leader>sq`       | 打开symbol窗口，并显示最后一次的symbols列表                                         |
| `<leader>sg`       | 使用当前光标下的单词作为搜索tag，列出所有匹配项                                  |
| `:SL <your-tag>` | 使用`<your-tag>` 作为搜索tag，列出所有匹配项                                             |

### 过滤

ex-symbols 将会列出搜索结果，类似下图：

![ex-symbol-window]({{site.url}}/docs/images/ex-symbol-window.png)

如果你通过`<leader>ss`，这里将会有太多的结果。ex-symbol 设计了类似于 [Global Search]({{site.url}}/docs/global-search)
的过滤命令。

ex-symbol允许我们使用Vim的搜索命令，比如`/`, `?`等等(更多信息请:help search-commands).
当你确认Vim的搜索模式后，你可以使用ex-symbol的过滤命令移除不想在symbol窗口显示的
结果。

| 命令            | 用法                                                                                                |
| :--------------- ---| :--------------------------------------------------------------------------------------------------- |
| `<leader>r`      | 移除symbol窗口中不包含Vim搜索模式的项                    |
| `<leader>d`      | 移除symbol窗口中包含Vim搜索模式的项                       |

更酷的是，你可以一边又一遍的过滤这个结果，直到剩下足够少结果用于选择。

### 确认搜索

通过按下`<Enter>`你将会选择ex-symbol的搜索。默认的，ex-symbol对所选符号使用`:ts`命令。
在ExVim中，如果ex-tags被安装，则使用`:TS`.

### 小技巧

**在任何地方使用 `<leader>sg`, `<leader>gg` 和`<leader>]` **

全局搜索命令 `<leader>sg`, `<leader>gg` 和 `<leader>]` 能够用于Vim中的所有buffer。
这个就意味着他们不仅仅能够用于编辑窗口，也能够用于插件窗口。

例如：

通过 `:GS foobar`执行搜索后. 在你的 "foobar" 结果窗口：

1. 你能过选择一个单词，通过`<leader>gg`再次搜索 . 
1. 通过 `<leader>]显示一个tag`
1. 通过`<leader>sg`显示symbol. 

在你的symbols列表中

1. 你能够确认一个选择
1. 你能够移至一个symbol，然后通过`<leader>gg` 搜索它

exVim所有的插件一起很好的协同工作。在windows下不用担心，当你做完全局的
ex-commands后，它们将会自动的关闭。

**使用`<leader>sg` 或 `:SL <your-tag>` 获取类成员**

当你在一个类名上面使用`<leader>sg`或`:SL <your-tag>`时，它将会为你显示此类及其成员。当你想查看
一个类的成员函数及变量时，是非常有用的。但是请记住，ex-symbol并不能够智能为你显示继承关系。

下面是我在一个C#工程中，使用`<leader>sg`获取"exSprite"类时的结果：

![ex-symbol-class-members]({{site.url}}/docs/images/ex-symbol-class-members.png)

**使用 `<leader>sg` 或 `:SL <your-tag>` 在不同的类中获取成员**

不像在一个类中浏览成员，你也可以使用 `<leader>sg` 和 `:SL <your-tag>` 在不同的类成员中得到相同的
定义。

例如，在一个c++工程中，你可以输入`:SL push_back`, 它将会为你显示不同类中的"push_back"函数。

![ex-symbol-different-class-members]({{site.url}}/docs/images/ex-symbol-different-class-members.png)

**使用完整symbol跳转替代`<leader>]` **

As we know `<leader>]` will list all possible tags defines and delcarations of the word under your cursor. 
That means you can't expect `<leader>]` list "ex::Array::push_back" since it is three words in Vim.
地球人都知道的，我们可以通过`<leader>]`列出当前光标下的单词所有可能的tags定义和声明。这
意味着你不能指望 `<leader>]`列出"ex::Array::push_back"，因为它在 Vim 中是有三个字。

这里有俩个办法解决此问题：一个是输入完整的定义 `:TS ex::Array::push_back`；二，我们在ex-symbol中
选择它。它将会使用完整的symbol作为你的`:TS`搜索模式。

![ex-symbol-different-class-members]({{site.url}}/docs/images/ex-symbol-different-class-members.png)

![ex-symbol-confirm-select]({{site.url}}/docs/images/ex-symbol-confirm-select.png)

