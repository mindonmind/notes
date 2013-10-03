Linux 下的网络管理工具
=====================

图形化管理工具
-------------

1. NetworkManager, nm-applet
2. Wcid

命令行
------

1. ifconfig

2. 无线：iwconfig, iwlist

如下命令可以通过命令行设置无线网络::

    su -
    ifconfig eth1 up
    iwconfig eth1 essid "teset" key xxxxxxxx
    dhclient eth1

使用 ``iwlist`` 可以查询更多无线信息，如::
    
    su -
    iwlist eth1 scan

参考
---

1. `Fixing Fedora's Wi-Fi with Wicd <http://www.techrepublic.com/blog/australia/fixing-fedoras-wi-fi-with-wicd/463>`_
2. `How to Configure Wireless on Any Linux Desktop <http://www.linux.com/learn/tutorials/374514-control-wireless-on-the-linux-desktop-with-these-tools>`_
3. `Quick HOWTO: Ch13 : Linux Wireless Networking <http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking>`_

