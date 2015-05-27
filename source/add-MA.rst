addMA
=====

描述
    给图表添加一个或多个移动平均线

用法
::

    addSMA(n = 10, on = 1, with.col = Cl, overlay = TRUE, col = "brown")
    addEMA(n = 10, wilder = FALSE, ratio=NULL, on = 1, with.col = Cl, overlay = TRUE, col = "blue")
    addWMA(n = 10, wts=1:n, on = 1, with.col = Cl, overlay = TRUE, col = "green")
    addDEMA(n = 10, on = 1, with.col = Cl, overlay = TRUE, col = "pink")
    addEVWMA(n = 10, on = 1, with.col = Cl, overlay = TRUE, col = "yellow")
    addZLEMA(n = 10, ratio=NULL, on = 1, with.col = Cl, overlay = TRUE, col = "red")

参数
    :n:         移动平均期数
    :wilder:    逻辑值，是否应用wilder
    :wts:       权重向量
    :ratio:     平滑/衰减比率
    :on:        应用到哪个图上（参考以下）
    :with.col:  使用数据的哪一列（参考以下）
    :overlay:   叠加绘制
    :col:       MA的颜色


详细
    查看TTR包中适当的MA函数获取详细信息和参考

返回值
    一个移动平均指标绘制在当前图表的新窗口，同时静默返回一个chobTA对象

参考
    查看TTR包中的MovingAverages

另见
    `addTA`_

范例
::

    ## Not run:
    addSMA()
    addEMA()
    addWMA()
    addDEMA()
    addEVWMA()
    addZLEMA()
    ## End(Not run)


