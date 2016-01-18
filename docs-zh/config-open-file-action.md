---
layout: docs
title: 自定义打开文件的行为
---

## 在ex-project中打开文件

在exvim中,你可以通过直接修改代码的形式自定义ex-project打开文件的行为.
主要通过编辑`ex-project/autoload/exproject.vim`, 找到`exproject#confirm_select`,添加你的代码.

## 在ctrlp中打开文件

ctrlp插件提供自定义的方式, 例子如下:

```vim
let g:ctrlp_open_func = { 'files': 'CustomOpenFunc' }
function! CustomOpenFunc(action, line)
    echomsg a:line
    let filetype = fnamemodify( a:line, ':e' )
    " echomsg filetype
    " silent echohl None

    if filetype == 'mp3'
        let playmp3cmd = 'mpg123'
        execute "silent !" .playmp3cmd.' '.a:line
        return
    elseif filetype == 'png'
        let imagecmd = 'gthumb'
        execute "silent !" .imagecmd.' '.a:line
        return
    elseif filetype == 'jpg'
        let imagecmd = 'gthumb'
        execute "slient !" .imagecmd.' '.a:line
        return
    else
        " Use CtrlP's default file opening function
        call call('ctrlp#acceptfile', [a:action, a:line])
    endif
endfunction
