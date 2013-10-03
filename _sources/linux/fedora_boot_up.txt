Fedora 启动过程
==============

不同体系结构的启动初始步骤互不相同，但一旦内核被加载完成，那么后面的启动过程在不同体系结构中都时一样的。

下面以x86机器为例说明 fedora 的启动过程。

BIOS
----

1. CPU在系统内存地址的最后面寻找BIOS(Basic Input/Output System)程序并将之执行。BIOS程序将引导后面的启动过程，此外，它还提供了访问外围设备的基础接口。因此，它常常被写入只读存储，并且总能够被使用。

2. BIOS检测系统以及其他外围设备。之后它选取引导设备,并将该设备的第一个扇区（又称为主引导记录，MBR）载入内存。该扇区仅有512字节大小，它包含了引导机器的一些机器码（boot loader）和分区表。剩下的引导过程将有boot loader执行。

Boot Loader
-----------

1. Boot Loader 可分为两部分，第一部分仅为一小段机器码，它负责将第二部分载入内存。

2. 当第二部分载入内存后，boot loader 根据配置文件列出可用的内核列表。用户选择后，boot loader在 ``/boot`` 目录找到相应的内核。之后，boot loader 载入一个或多个 ``initramfs`` 镜像至内存，内核需要用这些 ``initramfs`` 加载必须的驱动和相关模块。之后的引导过程由内核负责。

Kernel
------

1. 内核一旦被加载，它将对内存进行初始化及配置，同时设置好与系统相连的各种硬件设备，包括各处理器，输入输出子系统以及存储设备。

2. 接下来，内核到固定的地址寻找 ``initramfs`` ，并将其解压至 ``/sysroot/`` 。然后内存从中载入所有必须的驱动程序，并对与文件系统相关的虚拟设备进行初始化，比如 LVM 或软RAID。

3. 内核创建一个根设备，并释放所有可用内存。

4. 内核执行 ``/sbin/init`` 程序创建用户环境。

/sbin/init 程序
--------------

1. init 执行 /etc/rc.d/rc.sysinit 对系统进行初始化

2. init 根据 /etc/inittab 中指定的运行级别，执行 /etc/rc.d/rc<x>.d 中的所有服务，并称为这些自动执行的进程的父进程。这些服务也可以使用 ``service <command> start`` 或 ``/etc/init.d/<command> start`` 启动。

3. init 程序最后将执行 /etc/rc.d/rc.loacl 文件。

4. Upstart（一种 init daemon）根据运行级别所指定的每一个虚拟控制台分叉出一个 /sbin/mingetty 进程，这些进程打开与 tty 的通信通路，设置它们的模式，打印登录提示，接受用户名与密码，并初始化登录过程。如果运行在5级别，Upstart 调用 /etc/X11/prefdm 程序，它将选择相应的 X 显式管理器，比如gdm，kdm或xdm，由 /etc/sysconfig/desktop 文件指定。

附
----

1. 运行级别管理工具: chkconfig

2. 在启动时修改运行级别：在Grub启动界面输入 ``a <space><runlevel>``

3. XDM 负责用户验证，并启动 X 会话

参考
----
http://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/ch-boot-init-shutdown.html

