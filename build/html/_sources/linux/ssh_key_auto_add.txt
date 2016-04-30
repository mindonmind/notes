为ssh在首次运行时自动添加key
=============================

在使用ssh时常常需要为自己的key文件输入passphrase，而利用ssh-add命令可以将当前的key添加至ssh-agent中从而免除了后续的密码输入。

但每次开机使用ssh-add实在太麻烦，可以利用以下命令使得首次使用ssh时自动添加，前提是需要先安装好 ``keychain`` ::

    alias ssh='eval $(/usr/bin/keychain --eval --agents ssh -Q -q ~/.ssh/id_rsa) && ssh'

将它放入 ~/.bashrc 中即可正餐工作啦！

参考
https://wiki.archlinux.org/index.php/SSH_Keys
