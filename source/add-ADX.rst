addADX
======
描述
    添加ADX（动向）指标

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
    一个ADX指标绘制在当前图表的新窗口，同时静默返回一个chobTA对象

参考
    查看TTR包中的ADX

另见
    `addTA`_

范例
::

    ## Not run:
    addADX()
    ## End(Not run)

