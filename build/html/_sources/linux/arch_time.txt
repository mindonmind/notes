Arch Linux 时间显示不正确
=========================

先装了 Arch 之后又安装了 Windows，结果主板上的时间就华丽丽得被改快了十分钟。

解决方案如下：

1.首先修改 Windows 注册表，让其使用 ``UTC`` 时间::
   
   Windows Registry Editor Version 5.00

   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation]
      "RealTimeIsUniversal"=dword:00000001
      
将上边的内容粘贴至某后缀为 .reg 的文件，双击执行即可。

2.切换至 Arch，手工或利用 ntpd 将时间修改至当前正确时间，其中推荐 ntpd 方案::
   
   /etc/rc.d/openntpd start
   ntpd -s

3.时间正确后，将其写入 BIOS::

   hwclock -w

搞定。

--------

参考

http://bbs.archlinuxcn.org/viewtopic.php?id=424
