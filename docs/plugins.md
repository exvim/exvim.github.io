---
layout: docs
title: Plugins
---

For several years working with Vim. The exVim team get a good taste in choosing vim-plugins. 
We carefully select the plugins we need from Vim community. We also develop our own plugin in
demand, and for those plugins that stop maintaining by the author, we fork them into our 
organization and modify it to fit for exVim.

This article will show you the plugins currently used by default in exVim. I also recommend
you read [Select a plugin in the vim community]({{site.url}}/docs/select-your-plugin), which will teach you how
to search a plugin in the Vim world. 

## General

### Plugin Management

- [Vundle](https://github.com/gmarik/vundle)
- [Pathogen](https://github.com/tpope/vim-pathogen)
- [NeoBundle](https://github.com/Shougo/neobundle.vim)
- [Vimball](http://www.vim.org/scripts/script.php?script_id=1502)

Vundle needs you specified your plugin address in `.vimrc`, and install it by command 
`:PluginInstall`. After running the command, vundle will check the plugin and use git
download the latest version. You also can download the plugin manually without running
`:PluginInstall` command, in this way, it make you manage the plugin like pathogen.

Pathogen starts earlier than Vundle, and it is also great in manage your plugins. Pathogen
needs you manually download your plugins to the dest path, and once you done, you just need
one single line script in your `.vimrc` to make it load the plugins.

I didn't use NeoBundle so no comment for it.

Vimball is the most old plugin manager in Vim. It is not that great as the one I shows above.
I just want to introduce here so that new people from Vim not get confused with this plugins
and its file formation `*.vba`.

**My Choice**

Both Vundle and Pathogen do a great job. For Vundle, you need to write more script in your 
`.vimrc` to specified the plugins you wish to install, but Vundle will take care of all 
the rest things. For Pathogen, you just need one line in `.vimrc` but you have to manually 
run git or zip file for each plugin. I choose Vundle by default in exVim but also provide 
pathogen support. 

There is also some articles discuss this:

- http://jameslaicreative.com/moving-up-upgrading-from-pathogen-to-vundle/
- http://rmitc.org/2013/04/modern-vim-plugin-management-pathogen-vs-vundle/
- http://ryanpcarney.com/technologblog/goodbye-pathogen-hello-neobundle

### Status Bar

- [vim-airline](https://github.com/bling/vim-airline)
- [powerline](https://github.com/Lokaltog/powerline)
- [MiniBufExpl](https://github.com/techlivezheng/vim-plugin-minibufexpl)

Both of them make your Vim's status bar beautiful. Powerline needs python to make it run
in Vim, instead vim-airline is pure vim script. 

MiniBufExpl is an old plugin for shows the opened buffer like tab in other editor.  It 
stops developing for many years. The one I list is a forked version maintained by 
Techlive Zheng. He fixes some bugs in MiniBufExpl and make it better. 

**My Choice**

Since vim-airline written in pure vim script, it wins the battle in exVim plugins. 

### Quickly Open Files, Buffers and MRU

- [ctrlp](https://github.com/kien/ctrlp.vim)
- [unite](https://github.com/Shougo/unite.vim)

I only use ctrlp and it works great, so my choice is just ctrlp. unite looks great, and 
the author emphase that it is not a copy of ctrlp, it has other features. 

### Git Operation

- [vim-fugitive](https://github.com/tpope/vim-fugitive)
- [vim-gitgutter](https://github.com/airblade/vim-gitgutter)
- [vim-gist](https://github.com/mattn/gist-vim)

vim-fugitive is a great plugin to work with git. It use command to help you finish git commit,
diff and other task in Vim seamless.

vim-gitgutter diffs your current editing with your git files and show the differents in realtime 
in Vim.  I do like the idea but I seldom do that, I ues `:Gdiff` in vim-fugitive instead. Besides
realtime update may cause some lag, so I make this an option for user.

vim-gist is a plugin to upload your code or block to Gist.

### Undotree Management

- [undotree](https://github.com/mbbill/undotree)
- [gundo](https://github.com/sjl/gundo.vim)

Both plugin do the job to visual the Vim's undos in the window. 

**My Choice**

undotree do this better, it updates the undo nodes in the realtime when you edit file. It
also better in the code structure and less bug.

### File Browser

- [NERDTree](https://github.com/scrooloose/nerdtree)
- [ex-project](https://github.com/exvim/ex-project)

NERDTree is a real file browser in Vim. It browse files and folders just like a native file
browser. It also provide pattern to config files you don't like to show in the project.

ex-project is a plugin foucsed on only exVim's project file. It read the file and folder 
filter settings from `.exvim`, and create the project tree after that.

**My Choice**

Both of them can work together in exVim. I use NERDTree for editing files that not in project. 
But for project files, ex-project do it better. ex-project can create new files, folders directly
in the plugin window, and gives you the way to filter out folders you wish to ignore.

### Tag View For Current File

- [tagbar](https://github.com/majutsushi/tagbar)
- [taglist](http://www.vim.org/scripts/script.php?script_id=273)

TODO

### Easy Comment

- [NERDCommenter](https://github.com/scrooloose/nerdcommenter)
- [vim-commentary](https://github.com/tpope/vim-commentary)
- [tcomment](https://github.com/tomtom/tcomment_vim)
- [EnhCommentify](http://www.vim.org/scripts/script.php?script_id=23)

NERDCommenter don't need filetype for commenting, which is better.

### Code Complete

- [neocomplcache](https://github.com/Shougo/neocomplcache.vim)
- [neocomplete](https://github.com/Shougo/neocomplete.vim)
- [YouCompleteMe](https://github.com/Valloric/YouCompleteMe)
- [vim-autocomplpop](https://bitbucket.org/ns9tks/vim-autocomplpop/)
- [supertab](https://github.com/ervandew/supertab)

neocomplete is a new version of neocomplcache. But it needs your Vim build with +lua option.  
It provide faster complete function, however since it is not pure in Vim, most people still
choose neocomplcache.

YouCompleteMe looks great, and it saids it is the fastest complete engine in Vim. But it is
not pure in Vim.

vim-autocomplpop aka acp is an old plugin in Vim world. It is a pitty the author didn't put 
the plugin in Git. So I made this [fork version](https://github.com/exvim/ex-autocomplpop)

**My Choice**

I found neocomplcache in some case become much slow, that's why I still using vim-autocomplpop. 

### Code Snippet

- [neosnippet](https://github.com/Shougo/neosnippet.vim)
- [snipmate](https://github.com/msanders/snipmate.vim)
- [ultisnips](https://github.com/SirVer/ultisnips)

Havn't test them, no comment

There some great repository provide their snippets 

- https://github.com/spf13/snipmate-snippets
- https://github.com/scrooloose/snipmate-snippets
- https://github.com/honza/vim-snippets

### Syntax Check

- [syntasic](https://github.com/scrooloose/syntastic)

Syntasic is a really good plugin who will use your language lint programme to check your 
code.

### Easy text editing

- [vim-easymotion](https://github.com/Lokaltog/vim-easymotion)
- [vim-surround](https://github.com/tpope/vim-surround)
- [tabular](https://github.com/tpope/vim-surround)
- [showmarks](https://github.com/exvim/ex-showmarks)
- [visincr](https://github.com/exvim/ex-visincr)
- [matchit](https://github.com/exvim/ex-matchit)
- [LargeFile](https://github.com/vim-scripts/LargeFile)
- [AutoFenc](https://github.com/s3rvac/AutoFenc)

vim-easymotion is a powerful plugin enhance the use of Vim's `b`,`f`,`e`,`t`,... cursor moving 
commands.

vim-surround helps you easily add `(`,`{`,`[`,`"`,`'`,... signs.

tabular is a plugin help you align several text by signs such as `=`,`,`,... Very useful when
you writing json file or serveral variables in the code.

showmarks helps you showing the marks in your Vim.

visincr helps fill the number in order. very useful when editing code.

matchit enhance the Vim's `%` behaviour.

LargeFile allow you use simple rules opening large vim file

AutoFenc can detect file encoding automatically.

## Web Developer

### HTML

- [emmet-vim](https://github.com/mattn/emmet-vim)
- [vim-indent-guides](https://github.com/nathanaelkane/vim-indent-guides)

emmet-vim gives the power of editing html.

vim-indent-guides can shows indents for your file. I only use this when editing html, so I 
recommend it here.

### JavaScript, CoffeeScript, ...

- [vim-javascript](https://github.com/pangloss/vim-javascript)
- [vim-jsbeautify](https://github.com/maksimr/vim-jsbeautify)
- [vim-coffee-script](https://github.com/kchmck/vim-coffee-script)

vim-javascript includes the indent, syntax highlight for editing JavaScript.

vim-jsbeautify includes html, css, javascript indent and syntax highlight. I didn't use it
so no comment for this.

vim-coffee-script includes the indent, syntax highlight for editing CoffeeScript.

### JSON

- [vim-json](https://github.com/elzr/vim-json)

vim-json provides indent, syntax highlight for editing JSON file.

### Markdown

- [vim-markdown by plasticboy](https://github.com/plasticboy/vim-markdown)
- [vim-markdown by tpope](https://github.com/tpope/vim-markdown)

Both are good in providing markdown syntax highlight, indent and file detection. 

**My Choice**

I use plasticboy's vim-markdown. No reason, just the github stars.

### CSS

- [vim-less](https://github.com/groenewege/vim-less)
- [vim-css-color](https://github.com/skammer/vim-css-color)

vim-less provides syntax highlight for LESS.

vim-css-color will highlight your css color property as the color you filled. 
**But it is slow when editing large css file**

## C-lang Developer

### CRef

- [cref](https://github.com/exvim/ex-cref)

Nothing but quickly get manual for C functions. 

## Lua Developer

- [lua inspector](https://github.com/xolox/vim-lua-inspect)
- [lua-ftplugin](https://github.com/xolox/vim-lua-ftplugin)

## Go Developer

### Syntax highlight

- [go-lang](http://go-lang.cat-v.org/text-editors/vim/)
