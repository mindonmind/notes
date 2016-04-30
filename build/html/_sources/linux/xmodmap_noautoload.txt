xmodmap 无法自动加载设置
========================

::

    .xinitrc
    --------

    if [ -f $HOME/.xmodmap ]; then
        /usr/bin/xmodmap $HOME/.xmodmap
    fi

在 ``.xinitrc`` 里面加入上面几句后发现还是没有自动映射键盘，后来发现原来是 fcitx 把系统的键盘夺过去了。

直接把 fcitx 的 fcitx-xkb 选项关闭，即可。

参考
----

http://fcitx-im.org/wiki/FAQ#xmodmap_settings_being_overwritten
