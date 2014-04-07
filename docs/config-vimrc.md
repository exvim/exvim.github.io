---
layout: docs
title: Config .vimrc
---

# Config .vimrc

## .vimrc

TODO: the content in .vimrc

## .vimrc.plugins

TODO: what is .vimrc.plugins

## .vimrc.plugins.local

TODO: when will .vimrc.local execute? why this file?

## .vimrc.local

TODO: when will .vimrc.local execute? why this file?

Customise your guifont:

```vim
au! ex_gui_font " remove old set guifont event
set guifont=Consolas:h8:cANSI " set your font
```

Customise your vim-airline theme:

```vim
au VimEnter * exec 'AirlineTheme your_theme'
```

Close vim-airline

```vim
au VimEnter * exec 'AirlineToggle' " close vim-airline plugin
```
