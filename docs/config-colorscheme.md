---
layout: docs
title: Config Color Scheme
---

exVim's colorscheme consist three parts: your Vim colorscheme, exVim plugins' highlights and 
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

## Config exVim plugins' highlightings

exVim use [ex-aftercolor](https://github.com/exvim/ex-aftercolors) to config plugins' highlightings
after colorscheme changed. [ex-aftercolor](https://github.com/exvim/ex-aftercolors) will trigger  
color script in `after/` folder in the runtime path. More details, check 
[ex-aftercolor](https://github.com/exvim/ex-aftercolors) repo.

exVim puts its customization script in `vimfiles/bundle/ex-config/after/colors/`. By default
it supports [solarized](https://github.com/altercation/vim-colors-solarized) and exlightgray.

To customise with your own colorscheme, you must create a new file with the same name of your 
colorscheme in `after/colors` folder. There is three place you can put it:

1. vimfiles/bundle/ex-config/after/colors/ (Recommended if you choose **Method 1** in last section)
1. vimfiles/bundle/ex-colorschemes/after/colors/ (Recommended if you choose **Method 1** in last section)
1. vimfiles/after/colors/ (Recommended if you choose **Method 2** in last section)
1. your_own_color_bundle/after/colors/ (Recommended if you choose **Method 3** in last section)

Once you choose the place and create the file, take `vimfiles/bundle/ex-config/after/colors/solarized.vim` 
or `vimfiles/bundle/ex-config/after/colors/exlightgray.vim` as example to config your plugins' highlightings.

Here is a list of highlightings you can config in your aftercolor script:

| Name | Usage or reference |
| :---- | :---- |
| exConfirmLine | Color of selected line in ex-gsearch, ex-symbol, ... window |
| exTargetLine | Color of selected line in edit window |
| ex-showmakrs Highlighting | Check `:help showmarks-highlighting` |
| ex-easyhl Highlighting | Check `:help easyhl-highlighting` |
| ex-project Highlighting | Check `:help exproject-highlighting` |
| ex-gsearch Highlighting | Check `:help exgsearch-highlighting` |
| ex-symbol Highlighting | Check `:help exsymbol-highlighting` |

