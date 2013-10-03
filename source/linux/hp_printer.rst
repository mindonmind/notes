在 linux 下安装惠普打印机
=========================

需要安装 cups, hplip, hp-plugin::
    
    # pacman -S cups, hplip
    # yaourt -S hp-plugin

将当前用户加入 sys，lp 组::
    
    sudo gpasswd -a user lp
    sudo gpasswd -a user sys

启动 cupsd，并将其添加至系统服务中::
    
    sudo /etc/rc.d/cupsd restart

运行 hp-toolbox，添加打印机::

    hp-toolbox

参考
http://www.ai7.org/wp/html/920.html
