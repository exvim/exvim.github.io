---
layout: docs
title: Tags and Symbols
---

The Vim's tags system are quite useful for us. By the power of ctags, we can generate
the tags and analysis code with it in Vim.

exVim improve this by introduce the [ex-tags](http://github.com/exvim/ex-tags) 
and [ex-symbol](http://github.com/exvim/ex-symbol) plugins. exVim also integrate the
ctags generation in its `:Update` command.

## Tag Selection

In Vim we use `<ctrl-]>` and `:ts tag-name` to jump by tags. [ex-tags](http://github.com/exvim/ex-tags)
provides the same way but in different commands --- `<leader>]` and `:TS tag-name`.

You can think they are a polish version of the original.

For example, suppose we want to list the defines and declarations of dlmalloc, we 
type `:ts dlmalloc` and Vim give us:

![ex-tags-ts]({{site.baseurl}}docs/images/ex-tags-ts.png)

After that we have to type a number to select or press `<Esc>` to cancel it. 

In [ex-tags](http://github.com/exvim/ex-tags) we do this by `:TS dlmalloc` and Vim give us:

![ex-tags-ts2]({{site.baseurl}}docs/images/ex-tags-ts2.png)

Almost same as first one except this time you can move up and down by your cursor 
and can press `<Enter>` to select.

## Symbols

Symbols is the collection of tag names. In exVim's `:Update` command, after generate tags file
with ctags, it will read the tags, extracts the tag names into symbol file. This file a.k.a symbols   
will be used in [ex-symbol](http://github.com/exvim/ex-symbol) to help user fast search tags.

The symbols is very useful when you forget the exactly words in tags. It help you search from
the tag names, and allow you filter the result similar to the filter methods in 
[Global Search]({{site.baseurl}}docs/global-search).

### List symbols

ex-symbols provides you 4 different ways to list tags in the symbol window:

| Commands         | Usage                                                                                                |
| :--------------- | :--------------------------------------------------------------------------------------------------- |
| `<leader>ss`     | List all symbols in the symbol window.                                                               |
| `<leader>sq`     | Open symbol window and show the last listed symbols.                                                 |
| `<leader>sg`     | Use current word under the cursor as search tag, list all tags match it in the symbol window.        |
| `:SL <your-tag>` | Use `<your-tag>` as search tag, list all tags match it in the symbol window.                         |

### Filter

ex-symbols will list the search results like this:

![ex-symbol-window]({{site.baseurl}}docs/images/ex-symbol-window.png)

There is too many results if you list it all by `<leader>ss`. The ex-symbol design a very
similar search filter commands to [Global Search]({{site.baseurl}}docs/global-search).

ex-symbol allow user apply Vim's search commands such as `/`, `?` and so on (more details type :help search-commands).
After you confirm the Vim's search pattern, you can use ex-symbol's filter command to remove the
result you don't want in the symbol window.

| Commands         | Usage                                                                                                |
| :--------------- | :--------------------------------------------------------------------------------------------------- |
| `<leader>r`      | Remove the symbols listed in symbol window not contains the Vim's search pattern.                    |
| `<leader>d`      | Remove the symbols listed in symbol window contains the Vim's search pattern.                        |

The cool thing is, you can use these filter methods again and again till the result less 
enough to choose.

### Confirm the search

By pressing `<Enter>` you will confirm the ex-symbol searches. By default, ex-symbol use `:ts`
command on the selected symbol. exVim will change this to `:TS` if ex-tags installed.

### Tips

**use `<leader>sg`, `<leader>gg` and `<leader>]` everywhere**

The global commands such as `<leader>sg`, `<leader>gg` and `<leader>]` can be apply in all
the buffers in the Vim. This means they are not only can be used in edit-window, but also
plugin-windows. 

For example: 

Do a global search by `:GS foobar`. In your "foobar" result window, 

1. You can pick a word and search again by `<leader>gg`. 
1. You can show a tag by `<leader>]`
1. You can list a symbol by `<leader>sg`. 

In your listed symbols 

1. You can confirm the select 
1. You can move to a symbol and doing `<leader>gg` to global search it. 

exVim doing good in integrate all these plugins together. Don't worry about windows, they
will be closed automatically when you doing a global ex-commands.

**use `<leader>sg` or `:SL <your-tag>` get class members**

When you use `<leader>sg` or `:SL <your-tag>` in a current word which is a class name, it will bring you the 
list of the class and its members. This is very userful to check what's the functions and  
member variables in this class. But remember, ex-symbol not smart enough to bring you
the inherits. 

Here is what I get when I use <leader>sg in a class named “exSprite” in a csharp project:

![ex-symbol-class-members]({{site.baseurl}}docs/images/ex-symbol-class-members.png)

**use `<leader>sg` or `:SL <your-tag>` to check a member in different classes**

Unlike browsing members in one class, you can also use `<leader>sg` or `:SL <your-tag>` 
get same define in different members.

For example, you can type `:SL :push_back`, and it will show the ":push_back" function in 
different classes in a cpp project:

![ex-symbol-different-class-members]({{site.baseurl}}docs/images/ex-symbol-different-class-members.png)

**use the whole symbol jump instead of <leader>] jump**

As we know `<leader>]` will list all possible tags defines and delcarations of the word under your cursor. 
That means you can't expect `<leader>]` list "ex::Array::push_back" since it is three words in Vim.

There is two ways to solve this: One is type the whole define by `:TS ex::Array::push_back` or we can
choose it in ex-symbol. It will use the whole symbol as your search pattern in `:TS`.

![ex-symbol-different-class-members]({{site.baseurl}}docs/images/ex-symbol-different-class-members.png)

![ex-symbol-confirm-select]({{site.baseurl}}docs/images/ex-symbol-confirm-select.png)

