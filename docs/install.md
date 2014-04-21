---
layout: docs
title: Install
---

# Install

## Requirements

- Vim 7.3 or higher.
- [Vundle](https://github.com/gmarik/vundle) or [Pathogen](https://github.com/tpope/vim-pathogen)

## Install exVim

**NOTE:** 

exVim install **WILL NOT** overwrite your current Vim environment, this repository 
extract files, changes and running only in its repository directory. 

By the shell script `osx/mvim.sh` it provides, it will run Vim in its own environment 
without break your current Vim settings. This means you can preview, try and test exVim 
and decide later for replace or integrate with your current Vim. 

### Install in Mac OSX

1. Make sure the "mvim" command is available in your Terminal. To do this, type "mvim"
and check the result. If there is no "mvim" commands, you probably not install MacVim 
or you didn't make "mvim" as default command. You can download MacVim at 
https://code.google.com/p/macvim/. Extract the downloaded package find mvim file and put
it to /usr/local/bin

    ```bash
    cp mvim /usr/local/bin
    ```

1. Clone the repository to where you want: 

    ```bash
    git clone https://github.com/exvim/main
    ```

1. Execute the `osx/install.sh` shell script:

    ```bash
    cd main/
    sh osx/install.sh
    ```

    **NOTE:** The `osx/install.sh` only update vim-plugins in `main/` folder. 
    It **WILL NOT** overwrite your `~/.vimrc`, `~/.vim/` files, Don't worry about it.  

    After you running the script, the `main/` directory becomes a development environment
    for exVim. 
    
1. Preview exVim:

    ```bash
    sh osx/mvim.sh your/project/path/foobar.exvim 
    ```

### Install in Linux

1. Clone the repository to where you want: 

    ```bash
    git clone https://github.com/exvim/main
    ```

1. Execute the `unix/install.sh` shell script:

    ```bash
    cd main/
    sh unix/install.sh
    ```

    **NOTE:** The `unix/install.sh` only update vim-plugins in `main/` folder. 
    It **WILL NOT** overwrite your `~/.vimrc`, `~/.vim/` files, Don't worry about it.  

    After you running the script, the `main/` directory becomes a development environment
    for exVim. 
    
1. Preview exVim:

    ```bash
    sh unix/gvim.sh your/project/path/foobar.exvim 
    ```

### Install in Windows

1. Make sure the "vim" command is available in your batch command window. To do this, type "vim"
and check the result. If there is no "vim" commands, you probably not install gVim or you didn't 
put gVim install path to your Environment `PATH`. You can download gVim installer at 
[downloads]({{site.baseurl}}downloads) page. 

1. Follow this document [Vundle for Windows](https://github.com/gmarik/Vundle.vim/wiki/Vundle-for-Windows)
to setup Git and Curl.

1. Download the project by git or [zip file](https://github.com/exvim/main/archive/master.zip). 
Extract it on `C:\exVim` for example. 

    ```bash
    git clone https://github.com/exvim/main
    ```

1. Enter exVim folder, run `install.bat` batch file:

    ```
    C:\>cd exVim
    C:\exVim>call windows\install.bat
    ```

    After you running the script, the `C:\exVim` directory becomes a development environment for exVim. 

1. Preview exVim:

    ```
    C:\exVim>call windows\gvim.bat "d:\your\project\path\foobar.exvim"
    ```

## Replace your current Vim

If you like exVim, and want to run it directly without invoke preview commands, you can run the following
command:

```bash
# for mac user
sh osx/replace-my-vim.sh

# for linux user
sh unix/replace-my-vim.sh
```

If you are Windows user, you can do this in batch window: 

```
C:\exVim>call windows\replace-my-vim.bat
```

The commands above will do three things:

1. replace your `~/.vimrc` with exVim's `.vimrc`.
1. copy `.vimrc.plugins` to `~/.vimrc.plugins`.
1. copy and rename `vimfiles/` to `~/.vim/`.


**NOTE:** In Windows, the exVim's `.vimrc` also rewrite the runtimepath settings to make it search
`~/.vim` folder instead of `~/vimfiles`

## Install External Tools (Optional But Important)

Before we start exVim, we need some external tools to make it powerful. By default, exVim integrates:

- cTags ( for ex-tags, ex-symbol )
- id-utils ( for ex-gsearch )
- cscope ( for ex-cscope )

This external tools can be turn off in the `.exvim` file. To make the parsed result working with these
tools, exVim still need others such as:

- gawk
- sed

So we highly recommend you install the tools before [getting start with exVim]({{site.baseurl}}docs/getting-start). 

### Mac 

Mac users can use [Homebrew](http://brew.sh/) install them, just go to the [downloads]({{site.baseurl}}downloads) 
page and follow the commands in Mac section.

**NOTE:** If you already download XCode commands toolkit, you probably have an old version of cTags in it. 
You need to manually replace the old cTags with Homebrew's download.

### Linux ( Ubuntu, ... ) 

Ubuntu users can use `apt-get` to install them, just go to the [downloads]({{site.baseurl}}downloads) 
page and follow the commands in Mac section, change `brew` to `apt-get` instead.

### Windows

Windows users can install them by pre-compiled binaries. I provide most of them in [downloads]({{site.baseurl}}downloads)
page.

After download and extract the files, put them in your directory such as `C:\Users\Foobar\Bin`, and add 
this directory in your Environment `PATH`. Make sure all the commands are available in your 
batch command window.

## Install Powerline Font (Optional)

The exVim turn on the powerline font support by default. To make it work, you need to install 
powerline font to your system. 

We highly recommend DejaVuSansMono for Powerline. Just download [DejaVuSansMono-for-powerline.zip]({{site.baseurl}}downloads/DejaVuSansMono-for-powerline.zip),
unzip it and install all the `.ttf` file manually.

You can also select other powerline-font in [Lokaltog/powerline-fonts](https://github.com/Lokaltog/powerline-fonts)

If you think non of the fonts satisfy you, you can patch your favorite font by 
[fontpatching](https://powerline.readthedocs.org/en/latest/fontpatching.html) 
