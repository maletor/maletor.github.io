---
layout: post
title: Bundling Up With Vim
---

## Bundling Up With Vim

For my text editor I use [vim](http://vim.org). And with it I use a number of bundles to help simplify my life. Integrating with the editor saves time, requires less keystrokes and generally just makes it easier to process data.
With [vim-rails](https://github.com/tpope/vim-rails), I can switch between an action and its view or test with only two keystrokes. Also, I can cherry pick tests to run and have a quick fix list in a buffer for when they break.

Recently, I've discovered a wrapper for [git](http://git-scm.com/) known as [vim-fugitive](https://github.com/tpope/vim-fugitive). Using another simple workflow, I can generate a quick fix list of the result of git status.

Once that buffer is generated I can use
{% highlight bash linenos %}
D
q
Ctrl-w
Ctrl-k
{% endhighlight %}

You can repeat that for every staged file until everything looks good. Then I can choose to stage it for a commit with `-` on the filename in the buffer.
After everything is staged, I can commit with `C`, enter my haiku, and it is done.
Of relevance is a script which adds the branch name after the current directory listed in bash. This makes sense because operating in a different branch is (kind of) like a whole another subdirectory. It also shows whether the branch has uncommitted changes so you can quickly get a better idea of where you were last or what you are looking at.
Aliases for the subcommands are also nice.

And bash autocompletion for git is just icing on the cake. It works for:
* local and remote branch names
* local and remote tag names
* .git/remotes file names
* git 'subcommands'
* tree paths within 'ref:path/to/file' expressions
* common -long-options

Finally, here is a list of some of the plugins I use every day. And since they are just clones from a [GitHub](https://github.com) repository, updating them is as easy as a fast forward. You can read more in depth about these from their respective wiki pages and the manuals included with them.
* [pathogen](https://github.com/tpope/vim-pathogen) - keeps all these plugins organized in the .vim/bundle directory (as opposed to some twelve odd directories)
* [ack](https://github.com/mileszs/ack.vim) - like grep, but designed with large code repositories in mind (you can find out more at their website)
* [nerdcommenter](https://github.com/scrooloose/nerdcommenter) - 'nuff said
* [nerdtree](ttps://github.com/scrooloose/nerdtree) - visual file browser
* [snipmate](https://github.com/msanders/snipmate.vim) - akin to textmate's style of autocompletion
* [syntastic](https://github.com/scrooloose/syntastic) - provides a quickfix list when you save any file that has syntax errors
* [vim-endwise](https://github.com/tpope/vim-endwise) - figures out where an end needs to go and puts it there
* [vim-fugitive](https://github.com/tpope/vim-fugitive) - git wrapper
* [vim-ragtag](https://github.com/tpope/vim-ragtag) - shortcuts for a clunky ERB syntax
* [vim-supertab](https://github.com/tsaleh/vim-supertab) - smart, super smart autocompletion
* [vim-surround](https://github.com/tpope/vim-surround ) - surrounds text with html tags or ruby blocks or basically whatever you want
