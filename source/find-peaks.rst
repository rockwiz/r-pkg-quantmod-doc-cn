findPeaks
=========

描述
    发现给定序列峰（顶）/谷（底）的函数

用法
::

    findPeaks(x, thresh=0)
    findValleys(x, thresh=0)

参数
    :x:         一个时间序列或向量
    :thresh:    顶/底的最小阈值

返回值
    对应封顶/谷底的整数向量

    由于峰顶/谷底被定义为一个序列的最高/最低值，该函数
    As a peak[valley] is defined as the highest[lowest] value in a series, the function can only define it
    after a change in direction has occurred. This means that the function will always return the first
    period after the peak/valley of the data, so as not to accidentally induce a look-ahead bias.

范例
::

    findPeaks(sin(1:10))
    p <- findPeaks(sin(seq(1,10,.1)))
    sin(seq(1,10,.1))[p]
    plot(sin(seq(1,10,.1))[p])
    plot(sin(seq(1,10,.1)),type= l )
    points(p,sin(seq(1,10,.1))[p])

