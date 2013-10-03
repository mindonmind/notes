修改 Numpy 数组输出宽度及其他属性
=================================

在交互式使用 Numpy 进行数据分析时，常常需要将数组显示出来。但默认的输出格式有时不能满足我们的需要，比如输出宽度太窄导致有很多空间被浪费，且容易折行。

其实数组的输出属性都是可以定制的，能通过 `np.set_printoptions <http://docs.scipy.org/doc/numpy/reference/generated/numpy.set_printoptions.html>`_ 函数实现。

其中 ``precision`` 控制输出精度， ``linewidth`` 控制输出宽度。比如我们想将数组输出宽度调成 ``90`` ，可以写成::

    np.set_printoptions(linewidth=90)

这样显示出来的效果就好多了。
