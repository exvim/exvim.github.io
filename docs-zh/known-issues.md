---
layout: "docs-zh"
title: 已知问题
published: true
---

## 1.当使用命令 `:q` 关闭编辑中的文件时失去窗口

当你使用命令 `:q` 关闭编辑中的文件时，你可能遇到下面问题：

![known-issues-01]({{site.url}}/docs/images/known-issues-01.png)

为了解决这个问题，你只需要不使用 `:q` 命令，而用 `<leader>bd` 代替


快捷键 `<leader>bd` 在 `.vimrc.plugins` 中被定义成这样：

```vim
nnoremap <unique> <silent> <Leader>bd :EXbd<CR>
```

解决方案来自于 VimTip1119: 像 IDE 一样使用 Vim, 但是我改变了很多，已使得它在 exVim 的注册插件系统工作的更快更稳定

## 2. `:Update` 命令时失败

如果你使用 `:Update` 命令时看到如下的错误消息：

```
sed: -e expression #1, char 8: unterminated 's' command
```

```
gawk: xxx\vimfiles\tools\gawk\no-strip-symbol.awk:7: .... fatal: function `asort` not defined
```

这是由于你安装了老版本的 sed 和 gawk, 并且在环境变量中顺序优先于 exVim

这可能发生在你安装了 Git 和 Git Bash，为了解决这个问题，你只需要进入 Git 目录 (c:\Program Files (x86)\Git\bin\ by default), 然后重命名 gawk.exe 和 sed.exe 为其他任何名字

## 3. mkid: Can't read language map

如果你使用 mkid 时窗口出现如下提示：

```
mkid: can't read entire the language map file 'your/path/of/the/id-lang.map': No such 
file or directory
```

这是由于你指定的 `id-lang.map` 没有使用 `unix` 文件格式。你可以用 vim 打开文件并使用如下命令解决：

```vim
:set fileformat=unix 
```

然后保存它

## 4. mkid: Can’t create ID in C:\ in Windows

如果你使用 mkid 时窗口出现如下提示：

```
mkid: can’t get working directory: Permission denied
```

这可能是一个 Gnuwin32 id-utils 的 BUG，不能在 C:\ 创建 ID。我没有时间来 DEBUG mkid win32 的源码，所以目前的解决方案是把你的工程放在 D:\ 或其他根目录。 

如果你能修复这个 BUG，请一定，一定要告诉我.