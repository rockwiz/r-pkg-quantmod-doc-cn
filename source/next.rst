Next
====

描述
    将整个序列的所有项向前移动一个周期，周期1的值变成周期2的，周期2的变成周期3的，等等。滞后算子的相反运算，空白用NA填充

用法
::

    Next(x, k = 1)

    ## S3 method for class
    Next(x,k=1) quantmod.OHLC

    ## S3 method for class
    Next(x,k=1) zoo

    ## S3 method for class
    Next(x,k=1) data.frame

    ## S3 method for class
    Next(x,k=1)

参数
    :x:         要超前的向量或序列
    :k:         超前期数

详细
    把序列向前移动k个周期，在序列的末尾填上NA。特意设计用来在quantmod工作流中处理quantmod.OHLC和zoo序列。
    如果没有找到S3方法，将会调用base包中lag函数，反转索引以向前移动时序。

返回值
    原来的x序列后面加上k个NA，前置k个值缺失。返回的序列保持原来一样的观测点数目。不像Lag，k只允许一个值。

备注
    该函数的目的是获取希望预测的数据的“下一个”值，例如，股票t+1时刻的收盘价。具体而言，
    就是作为模型方程LHS的封装函数用于specifyModel的quantmod框架。

    它不是“魔术” - 因此不要期望得到明天的数值...

另见
    specifyModel Lag

范例
::

    Stock.Close <- c(102.12,102.62,100.12,103.00,103.87,103.12,105.12)
    Close.Dates <- as.Date(c(10660,10661,10662,10665,10666,10667,10668),origin="1970-01-01")
    Stock.Close <- zoo(Stock.Close,Close.Dates)
    Next(Stock.Close)       #one period ahead
    Next(Stock.Close,k=1)   #same

    merge(Next(Stock.Close),Stock.Close)

    ## Not run:
    # a simple way to build a model of next days
    # IBM close, given todays. Technically both
    # methods are equal, though the former is seen
    # as more intuitive...ymmv

    specifyModel(Next(Cl(IBM)) ~ Cl(IBM))
    specifyModel(Cl(IBM) ~ Lag(Cl(IBM)))

    ## End(Not run)


