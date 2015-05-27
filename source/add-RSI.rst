addRSI
======

描述
    给图表添加相对强弱指标（RSI）

用法
::

    addRSI(n = 14, maType = "EMA", wilder = TRUE)

参数
    :n:         DX计算期数
    :maType:    移动平均类型
    :wilder:    是否应用 *Welles wilder* 简易波动指标（EMA）

详细
    在TTR包中查看ADX的详细说明和参考

返回值
    An ADX indicator will be draw in a new window on the current chart. A chobTA object will be returned silently.

参考
    查看TTR包中的RSI

另见
    `addTA`_

范例
::

    ## Not run:
    addRSI()
    ## End(Not run)


