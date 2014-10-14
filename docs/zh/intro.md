---
layout: docs
title: 简介
---

TODO: 中文写下面的文档

 exvim是“把vim变成一个非常好的"集成开发环境"”的项目.exvim使得你可以在不同的项目上运用不同的设置,插件设置甚至插件. 从这个意义上说,exvim使vim变成世界上最好的IDE.


**更酷的是，我们使用exvim来开发exvim**

## 特性

- 用.exvim格式的配置文件来管理你的项目
- 用一个命令(:update)更新你的所有项目文件(tags,cscope-db,search-index,makefil, ...)
- 项目文件存放在一个文件夹(在文件夹.exvim.your_project_name下).
- 根据.exvim配置在不同的项目载入不同的插件
- Vim中更好的管理插件窗口.(避免多个插件窗口在Vim中混乱排列).
- 在项目窗口中浏览并编辑你的项目文件
- 类,变量,函数的标签跳转
- 在项目中使用全局搜索e. 
- 自定义全局搜索引擎(你可以选择grep,idutils甚至你自己的引擎)n one)
- 强大的全局搜索结果过滤t. 
- 可以画出类的继承关系图s. 
- 增强的quick-fix窗口
- 集成广受欢迎的Vim插件

## 怎么使用exvim?

编辑并保持你的项目配置在your_project_name.exvim文件中.用Vim打开它.然后Vim会在你的项目中自动的应用置配

配置包括:

- Vim的窗口位置(哪里是插件窗口,初始化打开的窗口,上一场窗口位置)t...)
- 文件和文件夹过滤
- 你希望在项目中使用的插件
- 项目的插件的配置
- 扩展工具,如grep,idutils,ctags,cscopepe,...
- 项目的扩展工具的配置.
- ...

exvim会确保你的项目文件在一个文件夹下(/.exvim.your_project_name/),这使得你的项目易于管理并且更好的利用扩展工具.如：

- 全局搜索目录及索引
- 标签(tags)
- cscope文件
- 层级目录
- 错误消息
- 临时文件
- ...

在exvim启动后,":update"命令会帮你自动更新所有项目文件es. 

##exvim如何挑选Vim插件?

exvim用纯粹的"Vim语言"来实现尽可能多的功能和特性.我们尽量避免重复造轮子,因此,我们精心选择和集成受欢迎的Vim-plugins社区.但是现存的Vim插件不能满足我们的需要.我们认为我们可以把这些缺乏的功能做的很好,所以我们自己开发并且把它放在了GitHub上 [exVim organization](https://github.com/exvim) on GitHub.

如下是我们选择Vim插件的标准:

- 仅用Vim脚本编写.
- 遵循UNIX哲学:do one thing well
- 尽可能少的依赖文件
- 高质量的代码和运行效率
- 比较活跃的社区
- 可以用插件管理器来安装.如Vundle ,pathogen structure)

阅读e [Plugins](http://exvim.github.io/docs/plu目录获取更多关于插件的信息
