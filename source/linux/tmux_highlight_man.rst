解决 Tmux 中 manpage 无法搜索高亮
==================================

在Tmux中使用manpage时发现在搜索某个关键词后并不会高亮显示，很是不方便，解决方案如下::

    $ mkdir $HOME/.terminfo/
    $ screen_terminfo="screen-256color"
    $ infocmp "$screen_terminfo" | sed \
      -e 's/^screen[^|]*|[^,]*,/screen-it|screen with italics support,/' \
      -e 's/%?%p1%t;3%/%?%p1%t;7%/' \
      -e 's/smso=[^,]*,/smso=\\E[7m,/' \
      -e 's/rmso=[^,]*,/rmso=\\E[27m,/' \
      -e '$s/$/ sitm=\\E[3m, ritm=\\E[23m,/' > /tmp/screen.terminfo
    $ tic /tmp/screen.terminfo

之后在 .tmux.conf 中加入::
    
    set -g default-terminal "screen-it"

参考：

http://tmux.git.sourceforge.net/git/gitweb.cgi?p=tmux/tmux;a=blob;f=FAQ
