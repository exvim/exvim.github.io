---
layout: docs
title: Project Window Usage
---

exVim use [ex-project](http://github.com/exvim/ex-project) browse project files by default. 
You can switch to NERDTree by press `<ctrl-Tab>` in the project window. You can also
make NERDTree as your default project tree by setting `project_browser` to `nerdtree`
in your `.exvim` file.

When you open exVim project, you will see:

![exvim-first-start-with-text]({{site.baseurl}}docs/images/exvim-first-start-with-text.png)

## Build Project Tree

In the chapter [Getting Start]({{site.baseurl}}getting-start) we've show you how to build project tree by 
ex-project plugins. Basically just move your cursor to project window, and press `<leader>R`.
The ex-project will build the tree like this:

![ex-project-tree]({{site.baseurl}}docs/images/ex-project-tree.png)

### Filter Folders

[ex-project](http://github.com/exvim/ex-project) allow you include or exclude first level
folders when building the project tree. exVim integrate this function in `.exvim` file.
Edit `your-project.exvim`, find the option `folder_filter_mode` and `folder_filter`. 

The `folder_filter_mode` accept value 'include' and 'exclude'. The `folder_filter` accept
the folder names in first level and separated by comma `,`. 

Suppose your first level directories are: *bin*, *src*, *tests*, *core*, *examples* and *docs*.
If you would like ex-project only build tree include src and core, you can set the option as:

```
folder_filter_mode = include
folder_filter += src,core
```

If you would like ex-project exclude *bin* and *test* directory but show others, you can write:

```
folder_filter_mode = exclude
folder_filter += bin,test
```

**Note:** To make it works, you need to save your `.exvim` changes, 
go to the project window and rebuild it. 

### Filter Files

You can also filter files by provide `file_filter` in `your-project.exvim`. The `file_filter`
option accept file suffixes separated by comma `,`. 

For example, if you want to show files with suffixes *.lua*, *.c* and *.h* in your project, 
set the `file_filter` as:

```
file_filter += lua,c,h
```

`file_filter` also accetps empty suffix by named it `__EMPTY__`, for example: 

```
file_filter += __EMPTY__,lua,c,h
```

This will allow files like LICENSE, README, Makefile, ... added to project tree.

**Note:** To make it works, you need to save your `.exvim` changes, 
go to the project window and rebuild it. 

For more details about file and folder filters, read [Config .exvim]({{site.baseurl}}config-project).

## Folding the folder
