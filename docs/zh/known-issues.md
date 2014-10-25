---
规划：文档
标题：简介
---

## 1.当使用命令':q'关闭编辑中的文件时失去窗口

When you use `:q` close a buffer in edit-window, you probably lose the window: 
当你使用命令':q'关闭编辑中的文件时，你可能遇到下面问题：

![known-issues-01]({{site.url}}/docs/images/known-issues-01.png)

为了解决这个问题，你只需要不使用':q'命令，而用'<leader>bd'代替


快捷键'<leader>bd'在'.vimrc.plugins'中被定义成这样：

```vim
nnoremap <unique> <silent> <Leader>bd :EXbd<CR>
```

The solution is come from the VimTip 1119: Use Vim like an IDE. 
But I changes a lot of to make it faster and stable with exVim's registry plugin system.
解决方案来自于VimTip1119；像IDE一样使用Vim
但是我改变了很多，已使得它在exVim的注册插件系统工作的更快更稳定

## 2. ':Update'命令时失败

If you running `:Update` command and see the following error messages:
如果你使用':Update'命令时看到如下的错误消息：

```
sed: -e expression #1, char 8: unterminated 's' command
```

```
gawk: xxx\vimfiles\tools\gawk\no-strip-symbol.awk:7: .... fatal: function `asort` not defined
```

这是由于你安装了老版本的sed和gawk,并且在环境变量中顺序优先于exVim

这可能发生在你安装了Git和Git Bash，为了解决这个问题，你只需要进入Git目录(c:\Program Files (x86)\Git\bin\ by default)
然后重命名gawk.exe和sed.exe为其他任何名字


## 3. mkid: Can't read language map

如果你使用mkid和meet时窗口出现如下提示：

```
mkid: can't read entire the language map file 'your/path/of/the/id-lang.map': No such 
file or directory
```

这是由于你指定的'id-lang.map'没有使用'unix'文件格式。你可以用vim打开文件并使用如下命令解决：

```vim
:set fileformat=unix 
```
然后保存它

## 4. mkid: Can’t create ID in C:\ in Windows

如果你使用mkid和meet时窗口出现如下提示：

```
mkid: can’t get working directory: Permission denied
```
这可能是一个Gnuwin32 id-utils的BUG，不能在C:\创建ID。我没有时间来DEBUG mkid win32的源码，所以
目前的解决方案是把你的工程放在D:\ 或其他根目录。 

如果你能修复这个BUG，请一定，一定要告诉我T^T
