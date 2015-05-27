addSMI
======

描述
    Add Stochastic Momentum Indicator to chart.

用法
::

    addSMI(n=13,slow=25,fast=2,signal=9,ma.type="EMA")

参数
    :n:         periods
    :slow:      slow
    :fast:      fast
    :signal:    signal
    :ma.type:   MA tyep to use, recycled as necessary

详细
    在TTR包中查看SMI的详细说明和参考

返回值
    An SMI indicator will be draw in a new window on the current chart. A chobTA object will be returned silently.

参考
    see SMI in TTR written by Josh Ulrich

另见
    `addTA`_

范例
::

    ## Not run:
    addSMI()
    ## End(Not run)

