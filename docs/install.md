---
layout: docs
title: Installation
---

# Install exVim

## Requirements

- Vim 7.3 or higher.
- [Vundle](https://github.com/gmarik/vundle) or [Pathogen](https://github.com/tpope/vim-pathogen)

## Install and Update

**NOTE:** 

exVim install **WILL NOT** overwrite your current Vim environment, this repository 
extract files, changes and running only in its repository directory. 

By the shell script `osx/mvim.sh` it provides, it will run Vim in its own environment 
without break your current Vim settings. This means you can preview, try and test exVim 
and decide later for replace or integrate with your current Vim. 

### Install in Mac OSX

1. Clone the repository to where you want: 

    ```
    git clone https://github.com/exvim/main
    ```

1. Execute the `osx/install.sh` shell script:

    ```
    cd main/
    sh osx/install.sh
    ```

    **NOTE:** The `osx/install.sh` only update vim-plugins in `main/` folder. 
    It **WILL NOT** overwrite your `~/.vimrc`, `~/.vim/` files, Don't worry about it.  

    After you running the script, the `main/` directory becomes a development environment
    for exVim. 
    
1. Preview exVim:

    ```
    sh osx/mvim.sh my_project.exvim 
    ```

1. Replace your current Vim:

    Like it? Want to replace it with your current Vim?  
    
    Now you've fall in love with exVim, and you want to replace it with your current
    Vim environment, just do:

    ```
    cd main/                           # enter the main/ repository
    cp .vimrc ~/.vimrc                 # you can merge your .vimrc with this
    cp .vimrc.plugins ~/.vimrc.plugins # the plugins settings for exVim, change it if you need
    cp -r vimfiles/ ~/.vim/            # replace your old plugins
    ```
    You can also replace it by running the script:

    ```
    sh osx/replace-my-vim.sh
    ```

### Install in Linux

1. Clone the repository to where you want: 

    ```
    git clone https://github.com/exvim/main
    ```

1. Execute the `unix/install.sh` shell script:

    ```
    cd main/
    sh unix/install.sh
    ```

    **NOTE:** The `unix/install.sh` only update vim-plugins in `main/` folder. 
    It **WILL NOT** overwrite your `~/.vimrc`, `~/.vim/` files, Don't worry about it.  

    After you running the script, the `main/` directory becomes a development environment
    for exVim. 
    
1. Preview exVim:

    ```
    sh unix/gvim.sh my_project.exvim 
    ```

1. Replace your current Vim:

    ```
    sh unix/replace-my-vim.sh
    ```

### Install in Windows

**NOTE:** If you're using msysgit, you can open the Git Bash shell and follow the
[install instruction for Linux](#install-in-linux) above.

1. Download the project by git or [zip file](https://github.com/exvim/main/archive/master.zip). 
Extract it on `C:\exVim` for example. 

1. Enter exVim folder, run `install.bat` batch file:

    ```
    C:\>cd exVim
    C:\exVim>call windows\install.bat
    ```
1. Wait for install finish 

    After you running the script, the `C:\exVim` directory becomes a development environment for exVim. 
    Preview exVim by:

    ```
    C:\exVim>call windows\gvim.bat my_project.exvim
    ```

    If you like it and want to replace it with your current Vim environment, copy the files
    below to your: 

    ```
    C:\exVim>call windows\replace-my-vim.bat
    ```

    **NOTE:** The exVim's .vimrc will rewrite the runtimepath settings for Windows, to make it search
~/.vim folder instead of ~/vimfiles

## Install Powerline Font

The exVim turn on the powerline font support by default. To make it work, you need to install 
powerline font to your system. 

exVim provide DejaVuSansMono for Powerline by default. Just enter the `ext/powerline-fonts/DejaVuSansMono/` 
directory in your exVim, and install all the `.ttf` file.

You can also select other powerline-font in [here](https://github.com/Lokaltog/powerline-fonts)

If you think non of the fonts satisfy you, you can patch your favorite font by 
[fontpatching](https://powerline.readthedocs.org/en/latest/fontpatching.html) 

