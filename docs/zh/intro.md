---
规划: 文档
标题: 简介
---

TODO: 中文写下面的文档

exVim is a project to turn Vim into a nice programming environment. This project makes you 
possible to apply different Vim settings, plugin settings and even plugins by different projects. 
In this way, it makes Vim become the best IDE in the world!
exVim是一个旨在改善vim成为一个优美的编辑环境的项目，让你能够使用不同的Vim设置，插件设置
甚至插件用于不同的工程成为可能。通俗的讲，就是为了使vim成为世界上最好的IDE。

**WHAT EVEN COOL IS --- WE USE EXVIM DEVELOP EXVIM! (\\(-_-)/)**
**更酷的是---我们能够使用exVim开发exVim(\\(-_-)/)**

## Features
## 特征

- Manage your project with `.exvim` setting file.
- Update your project files by single command. (tags, cscope-db, search-index, makefile, ...)
- Project files stores in one place (in the folder `./.exvim.your_project_name/` under your project).
- Load Vim-plugin on demand for different projects based on your `.exvim` settings.
- Better management of plugin windows in Vim. (avoid multiple plugin windows mess up in Vim)  
- Browse and operate your project files and folders in project window.
- Class, variable and function tags jumpping.
- Global search in project scope. 
- Global search engine customization (user can choose grep, idutils even his own one)
- A powful way to filter your global search result. 
- Generate classes hierarchy pictures. 
- Enhanced quick-fix window.
- Popular Vim-plugin integrated.
- 使用‘.exvim’配置文件管理你的工程
- 通过单一命令更新工程。(更新的东西有tags(自动补全用)，cscoped-db(查找用)，search-index, makefile,等等)
- 工程文件存储位置(在位于你的工程目录下的‘./.exvim.your_project_name/’文件夹下)
- 通过你的'.exvim'配置文件为不同的通过加载不同的插件配置
- 更好的插件管理，避免繁杂的插件导致vim的臃肿杂乱
- 通过工程窗口浏览和操作你的工程文件
- 提供健全的类，变量和函数跳转
- 支持工程范围内的全局搜索
- 支持自定义全局搜索引擎（用户可以使用grep，idutils甚至自己开发的搜索引擎）
- 提供强大的全局搜索结果过滤功能
- 可以生产类的集成图
- 增强版的quick-fix窗口
- 整合了流行实用的vim插件

## How does it work?
## 亲爱的她是怎么工作的呢？

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
