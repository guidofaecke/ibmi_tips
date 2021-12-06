# Setting BASH as your shell

Please make sure your home directory is set.
If you use Putty or SSH to open a connection to your IBMi and get this warning
```shell
Could not chdir to home directory /home/<your_username>: No such file or directory
```
Execute the following:
```shell
mkdir /home/<your_username>
chmod 750 /home/<your user_name>
```

## Option 1 (chsh - change shell)
Use `yum` to install `chsh`
```shell
yum install chsh
```
Switch to Bash
```shell
chsh -s /QOpenSys/pkgs/bin/bash
```

## Option 2 (via SQL)
Open a SQL command tool like `STRSQL` or `Run SQL Script` within ACS
```SQL
CALL QSYS2.SET_PASE_SHELL_INFO('*CURRENT', '/QOpenSys/pkgs/bin/bash')
```

##Option 3 (via regular shell)
Create a file called `.profile` in your home directory and add the following content
```shell
PATH=/QOpenSys/pkgs/bin:$PATH
export PATH
TERM=xterm
export TERM
exec bash
```