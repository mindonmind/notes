Pandas 中依据某 DataFrame 的 index 从另一 DataFrame 抽取信息
============================================================

如果不关心 index 的顺序是否变化，可以直接::

    df.merge(df1, 'left', left_index)

如果想保持 index 的顺序 merge 前后不变::

    df.reset_index().merge(df1.reset_index(), how='left', on='index').set_index('index')

或者直接创建一个新的 DataFrame::

    df = DataFrame(df1, index=[...])
