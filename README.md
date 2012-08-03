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

git enhanced branch completion
--------------------------------

Does the whole autocomplete thing and formats your terminal command line to include the current repo and branch you are working on.
Note that this is set up to work as is for OS X only.

*
* verify this file exists, /usr/local/git/contrib/completion/git-completion.bash .  The file should be installed with GIT utilities on OS X.
* copy the  code below into your .profile file.

     # Set git autocompletion and PS1 integration
     if [ -f /usr/local/git/contrib/completion/git-completion.bash ]; then
       . /usr/local/git/contrib/completion/git-completion.bash
     fi

     GIT_PS1_SHOWDIRTYSTATE=true

     if [ -f /opt/local/etc/bash_completion ]; then
         . /opt/local/etc/bash_completion
     fi
     PS1='\[\033[32m\]\u@\h\[\033[00m\]:\[\033[34m\]\w\[\033[31m\]$(__git_ps1)\[\033[00m\]\$ '

It should take effect for every new terminal window you open going forward.

For more information: http://en.newinstance.it/2010/05/23/git-autocompletion-and-enhanced-bash-prompt/

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
    
Have git remember your password
-------------------------------

https://help.github.com/articles/set-up-git