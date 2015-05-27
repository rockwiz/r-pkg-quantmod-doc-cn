addSAR
======

描述
    Add Parabolic Stop and Reversal indicator overlay to chart.

用法
::

    addSAR(accel = c(0.02, 0.2), col = "blue")

参数
    :accel:     Accelleration factors - see SAR
    :col:       color of points (optional)

详细
    在TTR包中查看SAR的详细说明和参考

返回值
    A SAR overlay will be drawn on the current chart. A chobTA object will be returned silently.

参考
    see SAR in TTR written by Josh Ulrich

另见
    `addTA`_

范例
::

    ## Not run:
    addSAR()
    ## End(Not run)

