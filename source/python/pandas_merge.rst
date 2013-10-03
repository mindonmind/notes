Pandas 中依据一个 DataFrame 的某列从另一个 DataFrame 中提取其他列的信息
=======================================================================

DataFrame 提供了 ``merge`` 方法来进行类似 ``SQL`` 数据库的 ``join`` 操作。
其中包括 ``inner``, ``outer``, ``left``, ``right`` join 等。

如果想百某个 DataFrame 里的 Colume 当作 Key 去另一 DataFrame 中抽取信息，可以使用 ``left join``::
    
    info = df.merge(b, 'left')

更多关于 ``join`` 操作的信息请参考: `A Visual Explanation of SQL Joins <http://www.codinghorror.com/blog/2007/10/a-visual-explanation-of-sql-joins.html>`_
