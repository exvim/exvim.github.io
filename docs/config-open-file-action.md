---
layout: docs
title: Config Open File Action
---

## Add open file action in ex-project

You can config the ex-project's open file action in exVim by directly modify the code in it.
Edit `ex-project/autoload/exproject.vim`, find the function define of `exproject#confirm_select`
and add your script there.

## Add open file action in ctrlp

The ctrlp plugin provide ways to let user config it. here is an example:

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
```
