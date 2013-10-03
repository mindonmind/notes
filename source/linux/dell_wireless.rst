让戴尔笔记本在 fedora 下用上无线网络
===================================

很多戴尔笔记本在安装了 linux 系统后都无法使用本机的无线网络，这个问题自从我第一次装 linux 时就一直困扰着我。

之前知道是因为 linux 缺少戴尔所采用的 Broadcam 无线网卡驱动所造成，但一直没能解决。

今天又查了一下，发现原来在 fedora 下已有相当简单的解决方案了。

1. 用 ``lspci`` 命令查看无线网卡型号，我的是 ``BCM4312``

2. 安装 ``rpmfusion`` 库::
   
    su -C 'yum localinstall --nogpgcheck http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm http://download1.rmpfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm

3. ``yum install kmod-wl``

4. 重启


参考：

1. `Install Broadcom wireless 802.11 driver in Fedora <http://www.howopensource.com/2011/08/install-broadcom-wireless-802-11-driver-in-fedora-15-14/>`_

2. `How do I get my wifi to work on my Dell wireless 1450?(broadcom) <http://ask.fedoraproject.org/question/367/how-do-i-get-my-wifi-to-work-on-my-dell-wireless>`_

3. `Is there a Fedora fix for the Dell Inspiron 1545 wireless problem? <http://ask.fedoraproject.org/question/1007/is-there-a-fedora-fix-for-the-dell-inspiron-1545>`_




