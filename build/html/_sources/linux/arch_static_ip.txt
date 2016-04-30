Arch Linux 静态 IP 设置
=======================

使用 ``netcfg`` ::

    pacman -S netcfg
    cp /etc/nework.d/example/ethernet-static /etc/network.d/eth0_static
    vi /eth0_static
    ... add ip, mask, gateway, DNS
    systemctl enable netcfg@eth0_static

参考

https://wiki.archlinux.org/index.php/Netcfg
