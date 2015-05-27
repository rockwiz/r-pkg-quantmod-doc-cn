addROC
======

描述
    给图表添加变动率指标

用法
::

    addROC(n = 1, type = c("discrete", "continuous"), col = "red")

参数
    :n:         期数
    :type:      复合类型
    :col:       线条颜色（可选）

详细
    在TTR包中查看ROC的详细说明和参考

返回值
    一个ROC指标绘制在当前图表的新窗口，同时静默返回一个chobTA对象。

参考
    查看TTR包中的ROC

另见
    `addTA`_

范例
::

    ## Not run:
    addROC()
    ## End(Not run)

