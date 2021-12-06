## Your default IBM i BASH prompt looks bland
Your BASH prompt looks like
```shell
~bash-5.1$
```
and you would like to spruce it up a bit.

### Option 1 - You are using GIT version control
Open or create the file `.bash_profile` in your home directory and add
```shell
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
export PS1="\u@\h \[\033[32m\]\w\[\033[33m\]\$(parse_git_branch)\[\033[00m\] $ "
```
### Option 2 - You are *not* using GIT version control
Open or create the file `.bash_profile` in your home directory and add
```shell
export PS1="\u@\h \[\033[32m\]\w\[\033[00m\] $ "
```

### Finally
Now save the file and execute
```shell
source .bash_profile
```

### Nothing happened - no change
In case nothing changed, move the above addition from `.bash_profile` to `.bashrc` and repeat
```shell
source .bash_profile
```

