---
layout: docs
title: Config Color Scheme
---

# Config Color Scheme

The exVim's colorscheme consist three parts: your Vim colorscheme, exVim plugins' highlights and 
plugin colorscheme configuration. To customise your colorscheme in exVim, you must follow the
steps below:

## Install your colorscheme

There is three place to install your colorscheme in exVim:

**Method 1. Install in ex-colorscheme (Recommended)**

It is recommended to install your colorscheme files in ex-colorscheme plugins. Just put your
colorscheme files under `vimfiles/bundle/ex-colorschemes/colors/`. Make sure you have installed
[ex-colorschemes](https://github.com/exvim/ex-colorschemes) plugins in your `.vimrc.plugins`.

**Method 2. Install in Vim's colors folder**

If you don't like to install ex-colorschemes, you can install your colorscheme as ordinary 
vim-plugins. Just put the file in `vimfiles/colors/` folder.

**Method 3. Install as vim-plugin bundle**

The method 2 didn't follow the structure of Vim's plugin managers' rules. We've used Vundle or
Pathogen so far, they also can help us manage our colors. 

Create your own plugin like [ex-colorschemes](https://github.com/exvim/ex-colorschemes), put your 
colorscheme script in it and upload it to Github. Put your Vundle script in `.vimrc.plugins.local`.

## Config exVim plugins' highlights

TODO:
