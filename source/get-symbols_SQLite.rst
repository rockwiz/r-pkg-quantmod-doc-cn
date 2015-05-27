getSymbols.SQLite
=================

描述
    Add Directional Movement Index

用法
::

    addADX(n = 14, maType="EMA", wilder=TRUE)

参数
    :n:         DX计算期数
    :maType:    移动平均类型
    :wilder:    是否应用 *Welles wilder* 简易波动指标（EMA）

详细
    在TTR包中查看ADX的详细说明和参考

返回值
    An ADX indicator will be draw in a new window on the current chart. A chobTA object will be returned silently.

参考
    see ADX in TTR written by Josh Ulrich

另见
    addTA

范例
::

    ## Not run:
    addADX()
    ## End(Not run)

