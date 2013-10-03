利用 Gzip 将 Python 对象进行压缩存储
====================================

利用 Python 进行数据分析时，常常需要将某个计算的结果存储到硬盘中，以免重复计算。一般采用的方法即利用 Python 自带的 Pickle 库将对象序列化并保存至某一文件中。但是，当数据对象占用内存较大时，数据的 IO 就会消耗很多时间，并占用大量硬盘空间。为此，我们可以利用 Gzip 库，对数据对象进行压缩存储。具体使用方式如下::

    import pickle
    import gzip

    def gload(filename):
        file = gzip.GzipFile(filename, 'rb')
        res = pickle.load(file, -1) 
        file.close()
        return res 

    def gdump(obj, filename):
        file = gzip.GzipFile(filename, 'wb')
        pickle.dump(obj, file, -1) 
        file.close()
    
