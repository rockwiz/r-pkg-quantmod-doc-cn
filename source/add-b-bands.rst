addBBands
=========

描述
    在当前图形上添加布林带

用法
::

    addBBands(n = 20, sd = 2, maType = "SMA", draw=bands , on = -1)

参数
    :n:         移动平均期数
    :maType:    移动平均类型
    :sd:        标准差数
    :draw:      indicator to draw: bands, percent, or width
    :on:        which figure area of chart to apply to


说明
    The primary addition to this function call over the TTR version is in the draw argument. ‘bands’ will
    draw standard Bollinger Bands, ‘percent’ will draw Bollinger %b and ‘width’ will draw Bolinger
    Bands Width. The last two will be drawn in new figure regions.

    See bollingerBands in TTR for specific details as to implementation and references.

返回值
    Bollinger Bands will be drawn, or scheduled to be drawn, on the current chart. If draw is either
    percent or width a new figure will be added to the current TA figures charted.

    一个ADX指标绘制在当前图表的新窗口，同时静默返回一个chobTA对象


    A chobTA object will be returned silently.

参考
    查看TTR包中的布林带

另见
    `addTA`_

范例
::

    ## Not run:
    addBBands()
    ## End(Not run)

