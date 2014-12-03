---
布局: 文档
标题: 开始
published: true
---

我们假设你已经完全安全了 exVim. 如果没有，请移至 [安装]({{site.url}}/docs/zh/install)。

## 生成 .exvim 工程文件

进入你的当前工作工程的根目录，比如：`~/foo/bar/foorbar/`。生成 .exvim 工程文件在这个目录(Mac下执行的命令如下)：

```bash
cd ~/foo/bar/foobar/
mvim foobar.exvim   # Linux and Windows user will use gvim instead. 
```

如果在 Windows 下，则可能是类似于下面的情况：

![exvim-first-start]({{site.url}}/docs/images/exvim-first-start.png)

![exvim-first-start-with-text]({{site.url}}/docs/images/exvim-first-start-with-text.png)

如果你检查你的工程目录，此目录下会存在一个隐藏文件夹，其命名为 `.exvim.foobar`。
这个文件夹包含所有的 `foobar.exvim` 工程在使用中需要的工程配置文件。

**注意事项:** 你能够创建多个 `.exvim` 文件在一个工程中。这就方便你为了不同的目的应用
使用不同的设置。

## 创建工程树

将光标移至左边的工程窗口 按下 `<leader>R` [[1]](#footnotes),
你将通过ex-project窗口看见你的工程文件，如下所示：
![exvim-with-project-tree]({{site.url}}/docs/images/exvim-with-project-tree.png)

你可以通过 `.exvim` 文件包含或者排除第一层目录。为了达到上述目的，你需要打开 `.exvim`
文件，找到包含 `folder_filter +=` 的行，然后设置它的选项。

比如：

```
folder_filter_mode = exclude
folder_filter += _build,_log,_ext
```

这里我选择了 `exclude` 模式，并且过滤掉此工程目录下的 `\build`, `\_log`, 和
`\_ext` 文件夹。当你完成此编辑，执行 `:w` 命令保存 `.exvim` 文件，这个操作会触发
exVim 刷新你的工程设置。

切换光标至你的 ex-project 窗口，然后通过 `<leader>R`[[1]](#footnotes) 重组你的工程树。

## 更新工程

通过执行 `:Update` 命令，你将会更新 exVim 工程(如下所示)：

![exvim-update-project]({{site.url}}/docs/images/exvim-update-project.png)

**注意事项:** Windows 用户将会看到一个弹出黑呼呼的窗口，然后刷出一串文字，就是
说明 exVim 在解析你的工程配置文件了，用于生成一些辅助文件。

默认的，exVim 将会使用如下工具剖析你的工程：

- cTags
- id-utils
- cscope
- ...

然后会生成一些文件保存在 `.exvim.foobar/` 文件夹下供 exVim 使用。这些文件将会供 exVim 插件使用，主要有：

- ex-project
- ex-gsearch
- ex-symobl
- ex-tags
- NERDTree
- AutoComplPop
- ...

一旦上述工作你完成，exVim 将会成为一个强有力的编程及分析工具，它会孜孜不倦的服务于你的工程。

**注意事项:** 当你改变你的工程司，你应该需要再次手动的去执行 `:Update` 命令，
exVim 使用静态的方式分析工程，它不会检测你的改变，这是由于我们认为性能是重要的，
并且根据我们的经验，手动执行 `:Update` 也不是很糟。

## 实用命令

现在你已经掌握了 exVim 基础，下面让我们快速测试一些功能：

| 命令             | 用处                                                                                                |
| :--------------- |:----------------------------------------------------------------------------|
| `<leader>gg`     | 全局搜索当前光标下的单词，并将结果展示在 ex-gsearch 窗口                      |
| `<leader>]`      | 搜索当前光标下的单词的定义及生命，并将结果展示在 ex-tags 窗口                 |
| `<leader>sg`     | 列出所有的当前单词的定义及生命，并将结果展示在 ex-symbol 窗口。              |
| `:GS <word>`     | 全局搜索 <word>                                                             |

在 ex-gsearch, ex-symbol 窗口，又可以通过 Vim 的 `/` 命令搜索一个模式段，并且通过
`<leader>r` 过滤搜索结果。记住，你可以在任意的 ex-plugin 窗口使用上面的命令，这
就意味着：

- 你能够在 ex-project 全局搜索一个单词
- 你能够在 gsearch 结果中列出 symbols 列表
- 你能够在 ex-symbol 窗口跳至一个tag
- ...

仅仅使用它们自在的过滤和定位你的最终结果。

更多关于 exVim 插件细节的介绍请阅读 [插件]({{site.url}}/docs/zh/plugins). 你也可以查看：
[ex-project](https://github.com/exvim/ex-project), 
[ex-gsearch](https://github.com/exvim/ex-gsearch),
[ex-symbol](https://github.com/exvim/ex-symbol),
... 获取每个插件的详细信息，和它们的配置。


<a name="footnotes"></a>
## 脚注

1. 这里 `<leader>R` 的意思是按下键 `\`, 紧接着按下 `shift`+`r` (大写的"r").
vim推荐第三方插件使用 `<leader>` (aka. `\`)开始你的操作，并且 vim 中的操作
是大小写敏感。