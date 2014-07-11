---
layout: docs
title: Config .exvim
---

exVim use [ex-vimentry](https://github.com/exvim/ex-vimentry) plugin to create and setup a project. 
The ex-vimentry will parse the files with suffix of `.exvim`, and apply the settings with your
hooked scripts.

## Syntax of .exvim file

Read [ex-vimentry syntax](https://github.com/exvim/ex-vimentry#syntax).

## Default Options

### folder_filter_mode (option)

Options:

- include 
- exclude

`folder_filter_mode` tell exVim which filter mode should be used for `folder_filter`. 

### folder_filter (array)

`folder_filter` accept folder names as value. The `folder_filter` will be used to filter 
out the folders in the first level of root directory. It will use the filter rule setted
in `folder_filter_mode`.

Example:

Suppose you have foo,bar,foobar,hello,world in your first level directory.

When you set the filter as: 

```
folder_filter_mode = include
folder_filter += foo,bar
```

Only foo,bar shows in your ex-project browser. 

When you set the filter as: 

```
folder_filter_mode = exclude
folder_filter += foo,bar
```

Only foobar,hello,world shows in your ex-project browser. 

This option affects the following plugins:

- ex-project 
- NERDTree
- ex-config
  - id-utils ( generate id-lang-autogen.map )
  - ctags (TODO)

### file_filter (array)

`file_filter` accepts suffix of the file you expect to browse and process in exVim project. 

Example:

```
file_filter += c,cpp
```

The filter above makes exVim accepts *.c, *.cpp files. 

`file_filter` also accetps empty suffix by named it `__EMPTY__`, for example: 

```
file_filter += __EMPTY__,c,cpp
```

The filter above also accepts files that doesn't have suffix, such as:
LICENSE, README, Makefile, ...

This option affects the following plugins:

- ex-project 
- NERDTree
- ex-config
  - id-utils ( generate id-lang-autogen.map )
  - ctags (TODO)

By default, if this option is empty, the id-utils will use `id-lang.map` in `tools/idutils/` for
creating ID. When this option setted, ex-config will create `id-lang-autogen.map` under your `.exvim.project/`
folder, and idutils will use it instead of `id-lang.map`.

### file_ignore_pattern (array)

`file_ignore_pattern` accepts filename patterns which will be ignored in exVim project.

Example:

```
file_ignore_pattern += useless.txt,*.min.js,_OLD_*.cpp
```

Which will make `useless.txt`, all files end with `.min.js` and all cpp files start from `_OLD_` be ignored.

Note the only wildcard character you can use is `*`.

## Post Init

When exVim finish parsed the `.exvim` file, it will invoke `g:exvim_post_init()` function if
it exists. You can define this function in you `.vimrc` file and customize your settings in it. 

Here is a (reference)[https://github.com/exvim/ex-vimentry#get-vimentry-settings] to guide you
use ex-vimentry functions in your script. 

## Multiple .exvim files

You can have multiple `.exvim` files in one project. This allow you to apply different 
settings for different purpose.
