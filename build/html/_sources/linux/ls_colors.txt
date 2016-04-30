ls 的输出颜色
=============

``ls`` 输出结果的配色由环境变量 ``LS_COLORS`` 指定。

它查询 ``$COLORS`` 指定的配色数据库(``/etc/DIR_COLORS``)后将结果输出。

用 ``dircolors`` 命令可以查看设置 ``$LS_COLORS`` 的具体方法。
