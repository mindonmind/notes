解决Unknown Terminal问题
========================

服务器上的 CentOS 版本较老，没有 rxvt-unicode-256color 的Terminfo文件。

解决办法是将本地的 terminfo 传之服务器::

    scp /usr/share/terminfo/r/rxvt-unicode-256color usr@server:~/.terminfo/r/

并在.bashrc中加入：

    export TERMINFO=$TERMINFO:~/.terminfo
