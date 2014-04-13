---
layout: docs
title: Config .vimrc
---

# Config .vimrc

exVim provide 4 different .vimrc files for users: `.vimrc`, `.vimrc.plugins`, `.vimrc.plugins.local`
and `.vimrc.local`. 

The first loaded file is `.vimrc`, we all familiar with it. Before `.vimrc` config your Vim, 
it will check if there is `.vimrc.plugins` in the same folder, and execute it. This is the 
default settings for exVim plugins. After `.vimrc.plugins` processed, the `.vimrc.plugins.local`
will be loaded if it exists. After that, `.vimrc` start its settings, and at the end, it will
check and load `.vimrc.local`.

## .vimrc

The structure of `.vimrc` in exVim can be divided into the following parts:

- setup encoding
- filetype off
- load `.vimrc.plugins` if exists
  - deafult plugins settings
- load `.vimrc.plugins.local` if exists
  - install your own plugins
  - customise plugins
- filetype on
- general settings
- visual settings
- Vim UI settings
- text edit settings
- auto commands
- key mappings
- load `.vimrc.local` if exists
  - customise
  - overwrite default settings

## .vimrc.plugins

This is the file for exVim config its default plugins.  

## .vimrc.plugins.local

This is where you can put your customise settings for plugins, and install the new plugins.
People may have questions such as: 

- Can we just put things in .vimrc.plugins?
- why we need .vimrc.plugins.local? 
- why don't we just use .vimrc.local instead? 

Basically, the `.vimrc.plugins.local` is here to prevent overwrite of `.vimrc.plugins`. In  
this way, you can keep the git changes and write your customization without worrying git updates. 

Since we use Vundle by default, it require plugin manage scripts write in the filetype off and on
block, that's why we have `.vimrc.plugins.local` and `.vimrc.local` together. The first one make
sure our plugin code in the filetype off and on block.

## .vimrc.local

There is a lot of things you can do in `.vimrc.local`, here are some frequency asks:

Customise your guifont:

```vim
au! ex_gui_font " remove old set guifont event
set guifont=Consolas:h8:cANSI " set your font
```

Customise your vim-airline theme:

```vim
au VimEnter * exec 'AirlineTheme your_theme'
```

Close vim-airline:

```vim
au VimEnter * exec 'AirlineToggle' " close vim-airline plugin
```
