在 Arch Linux 下安装 Enthought Python Distribution (EPD)
===========================================================

EPD 对学术界的支持力度真是不小啊，不仅一直提供了免费下载，最近甚至开始提供免费升级的 licenses 了！

下午在新的 Arch 下安装了 EPD，过程十分简单。

首先用edu邮箱申请下载地址并将安装包下至本地，之后用bash 执行即可。

装好后在使用 ipython 的时候出了一个小问题，原因是系统缺少 libpng12 这个库。

用 pacman 查询发现官方库里只有 libpng 1.5 版本，但在 archlinuxrp 库中惊喜的发现了 1.2 版，再次感谢 archlinuxrp :-)

安装完后便可以正常使用 ipython qtconsole 啦！


参考：

http://www.jz123.cn/text/0333918.html
