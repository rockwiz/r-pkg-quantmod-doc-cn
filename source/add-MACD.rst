addMACD
=======

描述
    给图表添加MACD（平滑异同移动平均线）指标

用法
::

    addMACD(fast = 12, slow = 26, signal = 9, type = "EMA", histogram = TRUE, col)

参数
    :fast:      快速移动平均线期数
    :slow:      慢速移动平均线期数
    :signal:    移动平均信号线期数
    :type:      MA（移动平均）类型。单个数值将被重复
    :histogram: 包括直方图
    :col:       线条颜色（可选）

详细
    在TTR包中查看MACD的详细说明和参考

返回值
    一个MACD指标绘制在当前图表的新窗口，同时静默返回一个chobTA对象

参考
    查看TTR包中的MACD

另见
    `addTA`_

范例
::

    ## Not run:
    addMACD()
    ## End(Not run)

