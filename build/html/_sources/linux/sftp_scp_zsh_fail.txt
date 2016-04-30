解决 sftp/scp 连接服务器无响应 (ssh 正常) 的问题
=================================================

这个问题出现了很久，后来发现是由于我使用的默认 login shell 为 zsh 导致的。

只要用 ::

    chsh -s /bin/bash

将默认的 login shell 改为 bash 即可。

但是我又不想从 zsh 切换回 bash，于是在 .bashrc 的最后添加如下两句::
    
    vt=$(fgconsole 2>/dev/null)
    (( vt != 1 )) && exec zsh

之所以这样写是因为我的 console 1 被设置为自动启用 startx，如果不判断一下， ``.xinitrc`` 里的 exec awesome 语句就无法起效（被覆盖）。


Update
------

实际原因是因为服务器端为了使用在本地编译的 zsh，我没有使用 ``chsh`` 命令修改默认 shell，而是在 ``.bashrc`` 的最后加上了::

    exec zsh

导致 sftp 等程序无法执行。
