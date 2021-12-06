## You are unable to log into SSH on IBM i older than 7.4
If your user profile is more than 8 characters long, you need to adjust a setting in sshd_config.
The `sshd_config` file can be found here:
```shell
/QOpenSys/QIBM/ProdData/SC1/OpenSSH/etc/sshd_config
```
Please find (and adjust) or add the following to `sshd_config`
```shell
ibmpaseforienv PASE_USRGRP_LIMITED=N
```
The next step is restarting SSHD
```shell
ENDTCPSVR SERVER(*SSHD)
STRTCPSVR SERVER(*SSHD)
```
