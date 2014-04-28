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

TODO:
