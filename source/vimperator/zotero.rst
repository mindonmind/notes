用 Vimperator 操控 Zotero 抓取文献或网页
========================================

将以下两行命令添加至 ``.vimperatorrc`` 文件中: ::

    map zo :emenu Tools.Zotero<CR>
    map zs :js Zotero_Browser.scrapeThisPage()<CR>
    map zp :js ZoteroPane.addItemFromPage()<CR>

以后就可以分别用 ``zo,zs,zp`` 这三个命令分别来打开 ``zotero``,抓取当前页面的文献,和从当前页面新建条目.

在抓取文献时有时会不想把当前页面的 ``snapshot`` 一起抓取,这时候可以在设置里面将 ``Automatically take snapshots when creating items from web pages`` 这一项去掉.但是这样做会是在从当前页面创建条目的时候也不创建 ``snapshot``,为此,可以将上面 ``zp`` 对应的那个命令做一些小修改,改成: ::

    map zp :js ZoteroPane.addItemFromPage('newpage', true)<CR>

这样,在使用 ``zs``, ``zp`` 命令的时候就都可以达到想要得到的结果.
