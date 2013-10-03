使用 zsh
==========

本机
^^^^

1. 安装 oh-my-zsh
2. 将.bashrc 的内容加入 .zshrc  
3. 切换默认 shell: ``chsh -s /bin/zsh``

服务器
^^^^^^

1. 安装 zsh 到自己的bin目录
2. 在.bashrc的最后加上一句 ``exec zsh`` 或者使用 3.
3. 使用 chsh 修改，前提是目标 zsh 在 ``/etc/shells`` 中
4. 如果使用 NIS，需要首先登陆主控机，使用 ``chsh`` 修改主控机上的 ``login shell`` ，然后再在其余任意一台机器中使用 ``ypchsh`` 修改。

