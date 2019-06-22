---
title: "Automating Git with Bash"
date: 2019-06-16T17:55:17+02:00
draft: false
---
I've been working with Git for this website more and more and after a time the "git commit" and "git push" gets a bit tedious(especially for small changes). Since we, sysadmins, like to automate things, it didn't take long to find a way to do just that.

This answer was inspired by [this answer](https://stackoverflow.com/questions/16709404/how-to-automate-the-commit-and-push-process-git) on Stackoverflow.

>Note. this guide is for systems with Bash. To make this work with other shells, you will have to set the alias in a different file.

The idea is to make a Bash shell script that will be run by an alias defined in the **~/.bash_aliases** file.

First we have create a directory and open the file:
```bash
$ mkdir ~/bin/
$ vim ~/bin/autogit.sh
```

Then we add the following code to the file and save it:
```bash
# Stage all changes, modifications, new files and deletions. Use "git add ." or "git add -u" when applicable.
git add -A

# Ask and store commit message in "$commitmessage".
echo 'Enter the commit message:'
read commitmessage

# Run git commit with "$commitmessage".
git commit -m "$commitmessage"

# Ask and store name of the branch in "$branch".
echo 'Enter the name of the branch:'
read branch

# Finally, push the commit to our "$branch".
git push origin $branch
```

Standard, this script will not get executable permissions, so we run:  
`$ chmod +x ~/bin/autogit.sh`

Now our file should run when we execute it. Our next step is to set up an alias.
Bash aliases should go in the **~/.bash_aliases** file, so we open/make it:  
`$ vim ~/.bash_aliases`

We add the following and save it:  
`alias gitcp='bash ~/bin/autogit.sh'`

To effectively use this alias, we have to read in the alias, by sourcing the **~/.bash_aliases** file:  
`$ source ~/.bashrc`  

>Are you wondering why we source **~/.bashrc** and not **~/.bash_aliases**? This is because **~/.bashrc** contains a reference to **~/.bash_aliases** and loads this file as well.  
After this, we should see our alias displayed when we run the **alias** command.
```bash
$ alias
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias gitcp='bash ~/bin/autogit.sh'
alias grep='grep --color=auto'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
alias ls='ls --color=auto'
```
Now you will automatically commit and push when you run **gitcp** in a Git repository.




