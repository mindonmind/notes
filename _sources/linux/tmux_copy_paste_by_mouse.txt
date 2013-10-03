Tmux 中使用鼠标选择复制与粘贴
==============================

如果想将在 Tmux 中发挥鼠标的威力，最好先将下面的设置打开::

    set -g mouse-resize-pane on
    set -g mouse-select-pane on
    set -g mouse-select-window on

    set -g mode-mouse on

以上设置，将允许用鼠标选择面板、窗口，并允许手动修改面板的大小。其中最后一条命令，允许利用鼠标进入 cope-mode，可以直接在 tmux 中滚动历史，并选择文本将其复制到 tmux 的缓冲区中。当想要在其他面板或窗口中复制这段文本时，只需要使用复制命令 ``bindkey p`` 即可。这样，基本上 Tmux 内部的复制粘贴就都可以搞定。

对于一个经常使用 Unix/Linux 系统的用户来说，肯定非常怀念传统的左键选择文本，中键复制文本的操作模式。但在以上设置下，会发现无法用中键向 tmux 中复制文本，也无法将 tmux 中选择好的文本中键复制到系统其他应用程序中。

这里有一个 trick，那就是在 tmux 中不论选择还是复制时，都按住 ``Shift`` 键，你会发现熟悉的中键又回来了 :-)
此外，还可以使用 ``Shift+Insert`` 快捷键将系统剪切板中的内容输入 tmux 中。
相对于 tmux 原生的选择模式（不加 ``shift`` 键），使用系统选择有个缺陷，即当一行内存在多个面板时，无法选择单个面板中的内容，这时就必须使用 tmux 自带的复制粘贴系统了。

参考：

http://awhan.wordpress.com/2012/04/18/tmux-copy-paste-with-mouse/

