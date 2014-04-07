---
layout: index
title: Home
---

# Welcome to exVim

exVim is a project to turn Vim into a nice programming environment. This project makes you 
possible to apply different Vim settings, plugin settings, even plugins for different projects. 
In this way, it makes Vim become the best IDE in the world!

**WHAT EVEN COOL IS --- WE USE EXVIM DEVELOP EXVIM! (\\(-_-)/)**

- [Downloads](downloads)
- [Install](docs/install)

## Features

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

After exVim started, type `:Update` command and exVim will helps you update project files. 
