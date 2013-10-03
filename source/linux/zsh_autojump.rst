autojump 与 zsh 自动补全
========================

`autojump <http://github.com/joelthelion/autojump>`_ 结合 zsh 绝对是路径跳转神器。

但要想借助 zsh 的自动补全发挥 autojump 的能力，还需要一点配置。

安装方法 ::

    git clone git://github.com/joelthelion/autojump.git
    cd autojump
    sudo ./install
    cp bin/_j ~/.oh-my-zsh/plugins/autojump
    
再将下面这行加入 ``.zshrc`` ::

    plugins = (auotjump)

如果不是使用的 ``oh-my-zsh`` ， 需要把 ``_j`` 文件复制到 zsh 的 ``$FPATH`` 中。
