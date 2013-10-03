解决Fedora下urxvt256c中ls显示不正常的问题
========================================

ls 命令会根据 $LS_COLORS 环境变量的值来将不同文件类型以不同的颜色、粗细显示。而LS_COLORS变量是系统根据/etc/DIR_COLORS数据库中的内容生成的。

而今天在Fedora 15中使用urxvt256c时目录显示却不加粗了，发现$LS_COLORS变量也为空。

后来发现问题是/etc/DIR_COLORS文件出了问题。

当使用urxvt256c时，$TERM变量会被设置为 ``rxvt-unicode-256color`` ，而在/etc/DIR_COLORS中被写成了 ``rxvt-unicode-256`` ，导致了系统无法在数据库中找到当前终端。

解决办法很简单，直接把 ``rxvt-unicode-256`` 改为 ``rxvt-unicode-256color`` 即可。或者将/etc/DIR_COLORS复制到~/.dir_colors，这样就不用修改系统文件了。

附送solarized版本的ls显示方案一枚：

https://github.com/seebi/dircolors-solarized


参考：

http://fedoraproject.org/wiki/Features/256_Color_Terminals
