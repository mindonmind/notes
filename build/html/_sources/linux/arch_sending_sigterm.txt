Arch Linux 关机时出现 "Sending SIGTERM To Processes  [Failed]"
==============================================================


原因是有某些进程没法正常退出，可以通过如下方法找到这些进程::

    sudo vim /etc/rc.d/fucntions

找到 ``kill_all()`` 函数，并在 ``start_fail`` 的上一行加入::

    /bin/bash

这样当系统关机无法结束进程时会进入 ``shell`` ，之后便可利用 ``ps`` 查看。

我这里发现是 ``NetworkManager`` 出现了问题，所以又改回原来的 ``network`` 服务了 :-(，或许哪天应该尝试一下 ``wicd`` 。

---------------

参考

https://bbs.archlinux.org/viewtopic.php?pid=1013033
