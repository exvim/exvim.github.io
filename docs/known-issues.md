---
layout: docs
title: Known Issues
---

## Loose window when use `:q` close buffer in edit window

When you use `:q` close a buffer in edit-window, you probably lose the window. To solve this
problem, just don't use `:q` in edit window. Instead of that, use `<leader>bd`.

The `<leader>bd` is defined in .vimrc.plugins in exVim: 

```vim
nnoremap <unique> <silent> <Leader>bd :EXbd<CR>
```

The solution is come from the VimTip 1119: Use Vim like an IDE. 
But I changes a lot of to make it faster and stable with exVim's registry plugin system.

## mkid: can't read language map

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

## mkid: Can’t create ID in C:\ in Windows

If you use mkid and meet the following message on Windows:

```
mkid: can’t get working directory: Permission denied
```
This is probably a bug for GnuWin32 id-utils, it can not create ID in C:\, 
I don’t have time to debug the mkid win32 souce code, so currently the solution 
is: Put you project in in D:\ or other volumn instead. 

If some one can fix this problem, please, please send us your patches! 
