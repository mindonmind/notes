用 Vimperator 操控 Readability
==============================

`Readability`_,又一个好用的浏览器拓展，可以让你更加舒适地进行网络阅读。

为了避免使用鼠标，可以通过设置快速标记(quickmarks)来使用 Vimperator 操控 Readability 所提供的功能。

首先，登录 `Readability`_ 并进入 `bookmarklets <http://www.readability.com/bookmarklets/>`_ 页面。这里可以看到 Readability 所提供的三个功能的链接（三段 js 代码）。

之后用 Vimperator 的复制链接命令::

    ;y n

将对应功能链接复制到剪切板，其中 ``n`` 对应某一功能书签的链接序号。然后即可以使用快速标记替代该链接::

    qmarks r <copied code>

下次想使用 Readability 阅读某网页时只需::

    gor

即可。

参考：

1. `vimperator+readability <https://mutelight.org/vimperator+readability>`_
2. `vimperator-firefox利器 <http://www.zfanw.com/blog/vimperator-firefox利器.html>`_

.. _Readability: http://www.readability.com
