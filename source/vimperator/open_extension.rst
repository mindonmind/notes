使用 Vimperator 打开拓展对话框或书签工具
========================================

在使用 vimperator 的过程中，常常会想打开某一拓展的对话框进行相关操作，比如用 evernote 抓取文章或打开 firebug 查看网页源码等。此外，当想将某一网页放入某一书签文件夹中时，也希望能打开 firefox 自带的书签工具进行操作。

这时可以使用 ``emenu`` 命令，如::

    emenu Bookmarks.Bookmark This Page
    emenu Tools.Add To Evernote
    emenu View.Firebug 
