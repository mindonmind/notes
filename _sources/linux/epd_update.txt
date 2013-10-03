EPD (Enthought Python Distribution) 更新命令
=============================================

EPD 采用 ``enpkg`` 命令进行整个系统与库的更新，常用的命令如下::

    enpkg epd  更新整个库
    enpkg --whats-new 查看有哪些包可以更新
    enpkg -s pkgs     查看包的可用版本
    enpkg pkg version    将包更新至某个版本，如果不指定version，则更新至最新版
