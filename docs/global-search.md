---
layout: docs
title: Global Search
---

exVim use [ex-gsearch](http://github.com/exvim/ex-gsearch) for global search. It also 
integrate the id-utils building pipeline which is required in ex-gsearch. In short, 
when you use `:Update` command, exVim will generate the ID file which will be used in 
ex-gsearch. 

## Search Text

[ex-gsearch](http://github.com/exvim/ex-gsearch) has two main ways for search text in 
your project.

 1. `<leader>gg`: It will search the current words under the cursor.
 1. `:GS <word>`: It will searcht the `<word>` you input in command line.

After search, ex-gsearch will list the result in the global search window. Press `<enter>`
on the result and exVim will jump to it in edit-window.

## Filter

ex-gsearch will show the search results as the picture show below:

![ex-gsearch-result]({{site.baseurl}}docs/images/ex-gsearch-result.png)

However, sometimes there will be too many search results and we would like to filter it.
ex-gsearch allow user apply Vim's search commands such as `/`, `?` and so on (more details type :help search-commands).
After you confirm the Vim's search pattern, you can use ex-gsearch's filter command filter the
result right in the global search window.

Each search result can divided into file part and content part, ex-gsearch 
provide four filter methods for different filter purpose: 

| Commands         | Usage                                                                                                |
| :--------------- | :--------------------------------------------------------------------------------------------------- |
| `<leader>r`      | Remove the search results in whiches content part not includes the Vim's search pattern.             |
| `<leader>d`      | Remove the search results in whiches content part includes the Vim's search pattern.                 |
| `<leader>fr`     | Remove the search results in whiches file part not includes the Vim's search pattern.                |
| `<leader>fd`     | Remove the search results in whiches file part includes the Vim's search pattern.                    |

The cool thing is, you can use these filter methods again and again till the result less 
enough to choose. For instance: 

 1. Try to `:GS test` and get the search result for 'test'. 
 1. We want only result with 'test foobar'. So try to search 'test foobar' by Vim's `/` in the search result window.
 1. Use `<leader>r` filter it.
 1. We want only file testXXX.js. Again try to search 'test\*.js' by Vim's `/` in the filtered results.
 1. Use `<leader>fr` filter it.
 1. ...

![ex-gsearch-filter]({{site.baseurl}}docs/images/ex-gsearch-filter.png)

You will get your search result after all.

## Tips

### Search by word

The `<leader>gg` and `:GS` command will search the text includes or equals to the words.
Sometimes we want the exactly words, not the part of them. You can use Vim's search pattern 
`\<word\>` in filter. But there is a quick way to do this. Just move your cursor to the search
title and press `gd`, Vim will automatically search the word under cursor and put it in between
`\<` and `\>` as search pattern.

### Get prev/next search results

The ex-gsearch's search result window is just a Vim buffer. Every time you search or filter
in it will make it record an undo history. You can use `u` and `<ctrl-r>` to get the prev or
next search result.

## Issues

The [Known Issues]({{site.baseurl}}docs/known-issues.md) #2 and #3 shows the issues of id-utils  
when working in Windows.

### When I use :GS search the text "foo::bar", it shows me nothing.

When you use `:GS` command search text such as "foobar.h", "foo::bar" and "foo.bar()".
It gets no result, but you are 100% that these words are contains in your code.

This is because ex-gsearch only accept **words**, which means you can not include symbols such as 
dot, comma even space in your `:GS` command.  

Instead of search the whold "foo::bar" pattern, we suggest you search "foo" first by `:GS foo`.
After that use ex-gsearch's filter method search the "foo::bar" and `<leader>r` to pick them.
