修改 fedora 的默认等宽字体
=========================

在 fedora 终端下面显示的中文十分难看，常常还会出现黑体、宋体夹着出现的情形。

研究了一会儿后发现与系统的等宽(monospace)字体配置有关。

如果想使用文泉驿正黑等宽作为最优默认等宽，可修改
``/etc/fonts/conf.d/65-nonlatin.conf`` 文件。

找到 ``<family>monospace</family>`` 后，在 ``<prefer>`` 下面添上一行::

    <family>WenQuanYi Zen Hei Mono</family>

这样终端的中文字体终于显示正常，而且浏览器显示代码快内的中文时也一样没有问题，真是舒服多了。

如果系统安装了文泉驿微米黑字体，还可已使用 ``WenQuanYi Micro Hei Mono``
代替上面的正黑等宽。
