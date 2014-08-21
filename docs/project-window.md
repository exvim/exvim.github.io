---
layout: docs
title: Project Window
---

exVim use [ex-project](http://github.com/exvim/ex-project) browse project files by default. 
You can switch to NERDTree by press `<ctrl-Tab>` in the project-window. You can also
make NERDTree as your default project tree by setting `project_browser` to `nerdtree`
in your `.exvim` file.

When you open exVim project, you will see:

![exvim-first-start-with-text]({{site.url}}/docs/images/exvim-first-start-with-text.png)

## Build Project Tree

In the chapter [Getting Start]({{site.url}}/docs/getting-start) we've show you how to build project tree by 
ex-project plugins. Basically just move your cursor to project-window, and press `<leader>R`.
The ex-project will build the tree like this:

![ex-project-tree]({{site.url}}/docs/images/ex-project-tree.png)

### Refresh single folder

Sometimes you just changes files in a single folder, using `<leader>R` to rebuild the 
whole project seems too heavy. Instead, we use `<leader>r` on it. It will only rebuild/refresh 
the folder under your cursor. 

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
go to the project-window and rebuild it. 

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
go to the project-window and rebuild it. 

For more details about file and folder filters, read [Config .exvim]({{site.url}}/docs/config-exvim).

## Folding the folder

You are able to fold a directory by moving the cursor to the line of the folder 
and press `<Enter>`. Press `<Enter>` again will unfold it.

![ex-project-folding]({{site.url}}/docs/images/ex-project-folding.png)

You can use the vim’s builtin fold command under project-window, for example:

 - Use `zO` and `zM` to fold up/close the whole project.
 - Use `zo` and `zc` to fold up/close current directory.
 - Use `zk` and `zj` to move between folds.

## Moving around in project-window

Basically you can use `h`,`j`,`k`,`l` and `arrow keys` moving in the project-window. ex-project
also provides `<ctrl-k>` and `<ctrl-j>` to help you fast jump between folders.

You may noticed, ex-project use `{` and `}` as its foldmarker:

![ex-project-foldmarker]({{site.url}}/docs/images/ex-project-foldmarker.png)

This means you can use fold jumping commands and mappings: 

 - Move your cursor to the start or end line of the fold, and press `%` to find the match of a fold.
 - Use `[{` and `]}` to jump to the prev or next fold. 


## Working with edit-window

### Edit file

When press `<enter>` on the file in project-window. ex-project will try to open the file in
your last edit edit-window. You can also split editing your file in edit-window 
by press `<shift-enter>`.

### Open file browser

When press `<shift-enter>` on the folder in project-window. ex-project will use the OS's file
browser, and open the folder in it. This is very useful when you trying to operate files 
in a folder.

### Locate your current file

If you are editing a file, and try to locate it in project-window. Just press `<leader>fc`. 
This operation will make ex-project search current edit file in edit-window and move the 
cursor to it in project-window.

## Create new file

To create a new file in project-window, move your cursor under a file or a folder line, 
then press `o`. ex-project will help you create a line like this:

![ex-project-new-file]({{site.url}}/docs/images/ex-project-new-file.png)

Type your filename and hit `<enter>` to open it in edit-window. Edit and save it by `:w` will  
create the new file.

## Create new folder

Create a new folder is more complicate than files. You must move your cursor under an exists
folder. This will make ex-project understand which folder you wish to your new folder to be
created in. After that, press `O` and the ex-project will ask you to type your folder name:

![ex-project-new-folder]({{site.url}}/docs/images/ex-project-new-folder.png)

When you input the name and hit enter confirm it, ex-project will immediately craete the  
new folder under the selected directory.

## Working with NERDTree

The best thing is ex-project can be works with NERDTree seamlessly. Move your cursor to
your project-window, and press `<ctrl-tab>`. ex-project will automatically switch to 
NERDTree. Even more, the `<leader>fc` mappings will also be applied to NERDTree. To swich
back, just press `<ctrl-tab>` again.

## Switch among .exvim projects

You may have multiple `.exvim` files in your project. And exVim supports switch project
dynamically. By open the different `.exvim` file, and explicitly save it with `:w`, exVim 
will switch to the new project.

![ex-project-multiple-exvim-files]({{site.url}}/docs/images/ex-project-multiple-exvim-files.png)
