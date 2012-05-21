git-tools
=========

Some git helpers to make git easier to use.

.gitconfig
--------------------------------

Adds pretty colors to your git output. Looks best with a black "Pro" terminal style.

To install this, copy the contents of the gitconfig, open your "~/.gitconfig" and paste these in. You can open your .gitconfig.

    edit ~/.gitconfig
    
git branch completion
-----------------------

Lets you tab complete your branch names on the command line.

* Copy the git-completion.sh file in this directory to your home directory and rename it to: .git-completion.sh
* Add "source ~/.git-completion.sh" to your .bash_profile file
* From the command line execute: "source ~/.bash_profile"

branch name in prompt
---------------------------

Displays the current branch name in your command line prompt.

* Drop the following into your .bash_profile to get the current git branch as part of your prompt. Feel free to customize the PS1 line.
* From the command line execute: "source ~/.bash_profile"

Here is the code:

    export PS1="\h:\W \u\[\e[1;36m\]\$(parse_git_branch)\[\e[0m\]$ " 

    parse_git_branch() {
     git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
    }
