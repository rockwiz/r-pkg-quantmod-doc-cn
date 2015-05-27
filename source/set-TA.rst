setTA
=====

描述
    用于chartSeries调用中管理TA参数

用法
::

    setTA(type = c("chartSeries", "barChart", "candleChart"))

    listTA(dev)

参数
    :type:  运用缺省TA的函数
    :dev:   显示TA参数的设备

详细
    setTA和unsetTA提供了为多个图表重用相同TA参数的简单途径。缺省地，所有绘图函数被设置为使用当前图表的缺省值。

    值得注意的是当前设备将被用来抽取TA参数列表去应用。这是通过内部调用listTA，随后调用适当函数的setDefaults来完成的。

    为紧随其后的图表设置缺省TA参数的另外的方法是通过setDefaults，参阅 *范例*

返回值
    利用为quantmod的绘图函数设置TA参数缺省值所产生的效果

备注
    直接用setDefaults需要将缺省TA调用向量包装到一次调用中替代以防止意外解析，或者调用listTA获取当前TA参数。后一种方式是setTA包装出的。

另见
    chartSeries addTA

范例
::

    ## Not run:

    listTA()
    setTA()

    # a longer way to accomplish the same
    setDefaults(chartSeries,TA=listTA())
    setDefaults(barCart,TA=listTA())
    setDefaults(candleChart,TA=listTA())

    setDefaults(chartSeries,TA=substitute(c(addVo(),addBBands())))
    ## End(Not run)


