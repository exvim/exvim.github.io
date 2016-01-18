---
layout: docs-zh
title: 安装
---

## 安装必备

- Vim 7.3 or higher.
- [Vundle](https://github.com/gmarik/vundle) or [Pathogen](https://github.com/tpope/vim-pathogen)

## 下载/更新exVim

**注意事项**

安装exVim将不会覆盖你已经存在的Vim环境，这个仓库所包含的文件，变化，仅仅运行在它自己
的文件夹。

通过提供的shell脚本`osx/mvim.sh`，它将会不破坏你现有的vim设置而运行exVim自己的环境设置。
这意味这你可以预览，尝试，及测试exvim，并且决定后面替换或者结合你的VIM。

**注意事项:**

对于Linux和苹果用户，如果你从[downloads]({{site.url}}/downloads)页面下载
**exVim**包，你可以忽略步骤1。
如果你从[下载]({{site.url}}/downloads)下载完整的exVim包，则可以忽略步骤1和2.

对于Windows用户，你可以[下载]({{site.url}}/downloads)“exVim Windows
安装包”, 如果你做了，那么你可以忽略本节。

### Mac上的下载/更新

1. 克隆仓库至你的目的地：
    ```bash
    git clone https://github.com/exvim/main
    ```

2. 执行'osx/install.sh' 脚本：
    ```bash
    cd main/
    sh osx/install.sh
    ```

    **注意:**`osx/install.sh` 仅仅更新`main/`文件夹里面的vim插件。
    并不会覆盖你的`~/.vimrc`,`~/.vim/`，不用担心哦！
    当你运行了这个脚本后，`main/`文件夹会变成一个exVim的开发环境！

1. 预览exVim

    ```bash
    sh osx/mvim.sh your/project/path/foobar.exvim 
    ```

    **注意:**你需要确定"mvim"命令在你的终端环境中是有效的。为此，执行"mvim"并查看
    结果。如果无"mvim"命令，你应该没有安装MacVim或者你没有使 "mvim"作为默认命令。
    你可以 http://code.google.com/p/macvim/. 从下载MacVim, 解压下载的包裹，找到
    mvim文件，并且将它放到 /usr/local/bin(执行下面命令).

    ```bash
    cp mvim /usr/local/bin
    ```

### Linux下的安装/更新

如果你从[下载]({{site.url}}/downloads)页面获取exVim主要的包，你可以忽略步骤1。
如果你从[下载]({{site.url}}/downloads)页面获取exVim完整包，你可以忽略步骤1和2。

1. 克隆仓库至你的里面目的地(执行下面命令)：

    ```bash
    git clone https://github.com/exvim/main
    ```

2. 执行"unix/insall.sh"脚本：

    ```bash
    cd main/
    sh unix/install.sh
    ```
    
    **注意:**`unix/install.sh`仅仅更新`main/`文件夹里面的vim插件。
    并不会覆盖你的`~/.vimrc`,`~/.vim/`，不用担心哦！
    当你运行了这个脚本后，`main/`文件夹会变成一个exVim的开发环境！

1. 预览exVim:

    ```bash
    sh unix/gvim.sh your/project/path/foobar.exvim 
    ```

### Windows下的下载/更新

1.确保vim命令在你的cmd窗口是可以运行的。为此，需要在cmd窗口执行vim命令，并且查看
结果。如果没有，可能你没有安装gvim或者你没有将gvim安装目录放到你的'PATH'环境里。
你可以下载gvim安装包，下载页面为：[下载]({{site.url}}/downloads)。

1. 参考文档[Vundle for Windows](https://github.com/gmarik/Vundle.vim/wiki/Vundle-for-Windows)
设置Git和Curl。

1. 下载exVim工程从git或者[zip file](https://github.com/exvim/main/archive/master.zip). 
并解压它到一个理想目录，比如`D:\exVim`。

    ```bash
    git clone https://github.com/exvim/main
    ```

1. 进入exVim文件夹，执行`install.bat`批处理文件

    ```
    C:\>cd exVim
    C:\exVim>call windows\install.bat
    ```

    执行此文件后，你的`D:\exVim`文件夹会成为一个exVim的开发环境。

    **注意:** 安装完成后可能需要重启电脑才能够使某些外部工具生效.

1. 预览exVim:

    ```
    C:\exVim>call windows\gvim.bat "d:\your\project\path\foobar.exvim"
    ```

## 安装exVim

如果你喜欢exVim，并且想直接运行它而不是通过预览命令，你可以使用下面的俩个选项：

### 选择1（推荐）：获取exVim并替换你当前的vim

建议你下载exVim至`~/exVim`目录。编辑你的vimrc文件，在Max/Linux下默认的是`~/.vimrc`,
在windows下是`C:\Users\your_name\_vimrc`。

在你的vimrc文件中，仅仅需要写：

```vim
let g:exvim_custom_path='~/exvim/'
source ~/exvim/.vimrc
```

现在你就可以直接运行exVim.

### 选择 2: 替换你当前的vim

为了替换你当前vim版本至exVim，你可以运行如下命令脚本：

```bash
# for mac user
sh osx/replace-my-vim.sh

# for linux user
sh unix/replace-my-vim.sh
```

如果你是windows用户，你可以运行下面的批处理脚本在当前命令窗口

```
D:\exVim>call windows\replace-my-vim.bat
```

上面的命令主要会做如下事情：

1. 用exVim的配置文件'.vimrc'替换`~/.vimrc`
1. 拷贝 `.vimrc.plugins` 至 `~/.vimrc.plugins`.
1. 拷贝并重命名 `vimfiles/` 至 `~/.vim/`.

**注意事项:** 在windows下，exVim的`.vimrc`还会重写运行路径的设置，以便它搜索
`~/.vim`文件夹而不是`~/vimfiles`。

## 安装外部工具(可选但重要)

在我们使用exVim之前，我必须安装一些外部工具，以便于exVim更强大。
默认的，exVim集成了：

- cTags ( for ex-tags, ex-symbol )
- id-utils ( for ex-gsearch )
- cscope ( for ex-cscope )

这些外部工具能够在`.exvim`工程配置文件关闭。为了使解析结果和这些外部工具协同工作，
exVim还需要其他，比如：

- gawk
- sed

所以我们强烈推荐你安装这些工具前阅读 [getting start with exVim]({{site.url}}/docs/getting-start). 

### Mac 

Mac用户能够使用 [Homebrew](http://brew.sh/) 安装他们, 跳至[下载]({{site.url}}/downloads) 页面，然后输入Max章节的相关命令。

**注意事项：**如果你已经下载了XCode的命令行工具包，你可能有一个旧版本的cTags。
你需要人为用Homebrew's 下载包将其替换掉。

### Linux ( Ubuntu, ... ) 
 
Ubuntu用户可以使用`apt-get`命令安装,跳至 [下载]({{site.url}}/downloads)页面，
参考Mac章节，然后使用`apt-get`命令替换掉`brew`命令即可！

### Windows


Windows用户可以使用预编译的二进制包进行安装. 我已经提供[下载]({{site.url}}/downloads)。

下载并解压这些文件，将它们放到你的理想目录，比如`C:\Users\Foobar\Bin`, 然后添加这个目录到你的环境变量`PATH`中，并确保他们在命令行窗口都是可以运行的。
**注意:** 一般安装这些二进制包,并加入到`PATH`后可能需要重启才能够生效.

## 安装Powerline字体(可选)

exVim默认是打开poweline字体支持的。为了使它工作，你必须在你的系统上安装Powerline字体。 

我们强烈推荐DejaVuSansMono字体，仅仅需要 下载[DejaVuSansMono-for-powerline.zip]({{site.url}}/downloads/DejaVuSansMono-for-powerline.zip)，
然后解压，手动安装`.ttf`文件。

你也可以挑选其他powerline-font字体 [Lokaltog/powerline-fonts](https://github.com/Lokaltog/powerline-fonts)

如果你认为没有一个字体让你满意，你也可以拼凑自己满意的字体
[fontpatching](https://powerline.readthedocs.org/en/latest/fontpatching.html) 
