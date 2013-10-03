vimperator hint 模式下忽略链接标号
==================================

有的时候希望通过直接输入链接名来打开链接，这时链接标号就容易形成阻碍。

解决办法是进入 ``escape mode`` ::

    :let mapleader = "\"

将上述语句加入 ``.vimperatorrc`` 后，在 hint 模式里敲击 ``\`` ，vimperator 就将不再用链接标号寻找链接。
