---
layout: docs
title: Known Issues
---

## 1. Loose window when use `:q` close buffer in edit window

When you use `:q` close a buffer in edit-window, you probably lose the window: 

![known-issues-01]({{site.url}}/docs/images/known-issues-01.png)

To solve this problem, just don't use `:q` in edit window. Instead of that, use `<leader>bd`.


The `<leader>bd` is defined in .vimrc.plugins in exVim: 

```vim
nnoremap <unique> <silent> <Leader>bd :EXbd<CR>
```

The solution is come from the VimTip 1119: Use Vim like an IDE. 
But I changes a lot of to make it faster and stable with exVim's registry plugin system.

## 2. Failed to :Update in Windows

If you running `:Update` command and see the following error messages:

```
sed: -e expression #1, char 8: unterminated 's' command
```

```
gawk: xxx\vimfiles\tools\gawk\no-strip-symbol.awk:7: .... fatal: function `asort` not defined
```

This is because you installed older version of sed and gawk in your PC, and their environment path has higher priority than exVim's. 

This often happends when you have Git and Git Bash installed. To fix the problem, just go to your Git directory (c:\Program Files (x86)\Git\bin\ by default), and rename the gawk.exe and sed.exe to something like _gawk.exe, _sed.exe.


## 3. mkid: Can't read language map

If you use mkid and meet the following message on Windows:

```
mkid: can't read entire the language map file 'your/path/of/the/id-lang.map': No such 
file or directory
```

This is because the `id-lang.map` you specified is not use the `unix` fileformat.
You can fix this by open the file in Vim and type:

```vim
:set fileformat=unix 
```
then save it.

## 4. mkid: Can’t create ID in C:\ in Windows

If you use mkid and meet the following message on Windows:

```
mkid: can’t get working directory: Permission denied
```
This is probably a bug for GnuWin32 id-utils, it can not create ID in C:\, 
I don’t have time to debug the mkid win32 souce code, so currently the solution 
is: Put you project in in D:\ or other volumn instead. 

If some one can fix this problem, please, please send us your patches! 
