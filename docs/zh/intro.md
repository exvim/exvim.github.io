---
layout: docs
title: 简介
---

TODO: 中文写下面的文档

 exvim是把vim变成一个非常好的"集成开发环境"的项目.exvim使得你可以在不同的项目上运用不同的设置,插件设置甚至插件. 从这个意义上说,exvim使vim变成世界上最好的IDE.


**更酷的是，我们使用exvim来开发exvim**

## 特性

- 用.exvim格式的配置文件来管理你的项目
- 用一个命令(:update)更新你的所有项目文件(tags,cscope-db,search-index,makefil, ...)
- 项目文件存放在一个文件夹(在文件夹.exvim.your_project_name下).
- 根据.exvim配置在不同的项目载入不同的插件
- Vim中更好的管理插件窗口.(避免多个插件窗口在Vim中混乱排列).
- Browse and operate your project files and folders in project window.
- Class, variable and function tags jumpping.
- Global search in project scope. 
- Global search engine customization (user can choose grep, idutils even his own one)
- A powful way to filter your global search result. 
- Generate classes hierarchy pictures. 
- Enhanced quick-fix window.
- Popular Vim-plugin integrated.

## How does it work?

Edit and saved your project settings in `your_project_name.exvim`, open it with Vim.
In this way exVim will parse the the file and apply settings to your project after Vim started.

The settings include:

- The window layout of your Vim. (Where to open the plugin window, initial opened window, last time layout...)
- File and Folder filter.
- Plugin you wish to use in the project.
- Plugin settings for the project.
- External tools. Such as grep, idutils, ctags, cscope,...
- External tools settings for the project.
- Your extension settings.
- ...

exVim also make sure project files stores in one place ( in the folder `./.exvim.your_project_name/` under your project ). 
This makes your project clean and much better work with external tools. These project files can be:

- global search index and results (idutils)
- tags
- cscope files
- hierarchy graph pictures
- error message
- temporary files
- ...

After exVim started, type `:Update` command, exVim will helps you update project files. 

## How does it integrate Vim-plugins?

exVim aims to implement as much as possible of the functions and features in **pure Vim language**. 
We try to avoid reinvent the wheel. As a result, we carefully select and integrate popular Vim-plugins 
in the Vim community. But the exists Vim plugins can't fulfill our needs. For those features lack of and 
for those features we think we can do it better, we develop by ourself in put them in 
the [exVim organization](https://github.com/exvim) on GitHub.

Here is the standards we pick, patches and develop for a vim-plugin:

- Develop by pure Vim language
- Follow the unix philosophy: do one thing well 
- Less dependencies 
- High quality of the code and good performance
- Highly active community
- Can be installed with a variety of plugin managers, Vundle or pathogen. (Repo in GitHub, standard runtime path structure)

Read the [Plugins](http://exvim.github.io/docs/plugins/) to get the details of the plugins
in exVim.
