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
1. Wait for install finish 

    After you running the script, the `C:\exVim` directory becomes a development environment for exVim. 
    Preview exVim by:

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

## Install Powerline Font

The exVim turn on the powerline font support by default. To make it work, you need to install 
powerline font to your system. 

We highly recommend DejaVuSansMono for Powerline. Just download [DejaVuSansMono-for-powerline.zip]({{site.baseurl}}downloads/DejaVuSansMono-for-powerline.zip),
unzip it and install all the `.ttf` file manually.

You can also select other powerline-font in [Lokaltog/powerline-fonts](https://github.com/Lokaltog/powerline-fonts)

If you think non of the fonts satisfy you, you can patch your favorite font by 
[fontpatching](https://powerline.readthedocs.org/en/latest/fontpatching.html) 

## Install External Tools
