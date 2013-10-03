修改 Gnome 标题栏宽度与标题栏的隐藏
==================================

Fedora 中的标题栏过宽的问题一直为人诟病，而带着个标题栏的 firefox 更是占用了不少网页空间。

还好，在 Gnome 中可以方便地对其进行配置。

1. 修改标题栏宽度::

   sudo vim /usr/share/themes/Adwaita/metacity-1/metacity-theme-3.xml
   :/title_vertical_pad/s/value="[0-9]\{1,}"/value="0"/g    # 将标题栏宽度设为0

2. 最大化时隐藏标题栏::

   sudo vim /usr/share/themes/Adwaita/metacity-1/metacity-theme-3.xml
   /frame_geometry name="max"
   :s/>/ has_title="false">/

3. 重启 Gnome::

   Alt+F2
   r
