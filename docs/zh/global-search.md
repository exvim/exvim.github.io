---
布局：文档
标题：全局搜索
---

exVim使用[ex-gsearch](http://github.com/exvim/ex-gsearch)进行全局搜索。它也在必要
时候和id-utils创建的管道协同工作。总之，当你使用`:Update`后，exVim将会生成被
ex-gsearch使用的ID文件。
**注意事项: ** 如果不能搜索,首先看你这个ID文件是否已经生成!

## 查找文本

[ex-gsearch](http://github.com/exvim/ex-gsearch)有俩个主要的方式可以在你的工程中
搜索文本。

 1. `<leader>gg`: 将会搜索光标下的单词。
 1. `:GS <word>`: 将会搜索`<word>`或包含`<word>`的文本
 1. `:GSW <word>`:将会搜索完整的`<word>`

搜索结束后，ex-gsearch将会在全局搜索窗口列出搜索结果。选中搜索项，按下`<enter>`
键，编辑窗口将会跳至对应处,你可以通过按下**<ES>**按键关闭搜索窗口!

**注意: **自己修改这个关闭窗口的快捷键,如下:
`call exgsearch#register_hotkey( 2, 1, 'q', ":EXGSearchClose<CR>" , 'Close window.')`

## 过滤

ex-gsearch 将会展示如下所示的搜索结果：

![ex-gsearch-result]({{site.url}}/docs/images/ex-gsearch-result.png)

无论如何，有时这里会有很多的结果，我们可能希望过滤它们。es-gsearch允许我们使用Vim
的搜索模式，比如`/`,`?`等等(更多的可以查看vim的搜索相关的帮助文档)。在你确认vim的
搜索模式后，你就可以使用ex-gsearch的过滤命令在搜索窗口过滤出正确的结果。

每个搜索结果都可以分为文件部分和文本部分，ex-gsearch针对不同的过滤目的提供了不同
的过滤方法：

| 命令             | 用途                                                       |
|:---------------- | :----------------------------------------------------------|
| `<leader>r`      | 移除搜索结果中文本部分不包含vim搜索模式中所包含的。        |
| `<leader>d`      | 移除搜索结果中文本部分包含搜索模式包含的。                 |
| `<leader>fr`     | 移除搜索结果中文件部分不包含vim搜索模式中所包含的。        |
| `<leader>fd`     | 移除搜索结果中文件部分包含搜索模式包含的。                 |

比较酷的是，你可以使用这种方法一边又一边的过滤，直到结果是你想要的为止。例如：

 1. 测试`:GS test`, 获取关于`test`的搜索结果。
 1. 我们理想中的结果只是`test foobar`。所以我们在搜索结果窗口中使用vim的`/`模式搜索`test foobar`.
 1. 使用`<leader>r`过滤它。
 1. 我们只想过滤文件testXXX.js。再一次在已经过滤的结果中使用vim的`/`搜索`test\*.js`.
 1. 使用`<leader>fr`过滤它.
 1. ...

![ex-gsearch-filter]({{site.url}}/docs/images/ex-gsearch-filter.png)

做完这一切后你就会获取最终结果了。

## 小窍门

### 搜索单词

`<leader>gg`和`:GS`命令都将会搜索包含或者等价于此单词的文本。有时候你只想搜索此单
词，此时，你可以使用Vim的搜索模式`\<word\>`在过滤命令中。但是exvim给你提供了更快捷
的方法，将光标移动到搜索标题那里，按下`gd`，vim将会自动将光标下的单词放入`\<`和`\>`
中间作为搜索模式进行单词搜索。

### 获取上一次/下一次搜索结果

ex-gsearch的搜索结果窗口仅仅是一个vimbuffer。每次你搜索或过滤它都会使它重新记录并
生成撤销历史。你可以使用`u`和`<ctrl-r>`获取上次或者下次的搜索结果。

## 问题

已知问题#2和#3展示了id-utils在windows下面工作时候的问题。

### 当我使用使用 :GS 搜索文本"foo::bar"时，它什么都没有显示.

当你使用文本，比如"foobar.h","foo::bar"和"foo.bar()"，你没有获取到结果，但是你又
100%确定这单词是包含在你的代码中。

原因可能是ex-gsearch仅仅接受**words**,这个就意外着你不能在你的`:GS`命令中包含',',
'.'甚至空格。

为了获取完整的"foo::bar"模式，我们建议你首先使用":GS foo"。然后使用ex-gsearch的过
滤命令进行过滤以获取最终结果。
