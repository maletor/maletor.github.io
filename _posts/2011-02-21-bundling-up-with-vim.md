---
layout: default
title: Bundling Up With Vim
---

# {{ page.title }}
#### February 21, 2011

For my text editor I use vim. And with it I use a number of bundles to help simplify my life. Integrating with the editor saves time, requires less keystrokes and generally just makes it easier to process data.
With vim-rails, I can switch between an action and its view or test with only two keystrokes. Also, I can cherry pick tests to run and have a quick fix list in a buffer for when they break.

Recently, I’ve discovered a wrapper for git known as vim-fugitive. Using another simple workflow, I can generate a quick fix list of the result of git status.

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

And bash autocompletion for git is just the coup de grâce. It works for:
* local and remote branch names
* local and remote tag names
* .git/remotes file names
* git ‘subcommands’
* tree paths within ‘ref:path/to/file’ expressions
* common —long-options

Finally, here is a list of some of the plugins I use every day. And since they are just clones from a GitHub repository, updating them is as easy as a fast forward. You can read more in depth about these from their respective wiki pages and the manuals included with them.
* pathogen – keeps all these plugins organized in the .vim/bundle directory (as opposed to some twelve odd directories)
* ack – like grep, but designed with large code repositories in mind (you can find out more at their website)
* nerdcommenter – ’nuff said
* nerdtree – visual file browser
* snipmate – akin to textmate’s style of autocompletion
* syntastic – provides a quickfix list when you save any file that has syntax errors
* vim-endwise – figures out where an end needs to go and puts it there
* vim-fugitive – git wrapper
* vim-ragtag – shortcuts for a clunky ERB syntax
* vim-supertab – smart, super smart autocompletion
* vim-surround – surrounds text with html tags or ruby blocks or basically whatever you want
