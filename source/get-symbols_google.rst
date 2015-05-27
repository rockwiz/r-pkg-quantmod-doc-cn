getSymbols.google
=================

描述
    Downloads Symbols to specified env from ‘finance.google.com’. This method is not to be called directly, instead a call to getSymbols(Symbols,src= google ) will in turn call this method. It is documented for the sole purpose of highlighting the arguments accepted, and to serve as a guide to creating additional getSymbols ‘methods’.

用法
::

    getSymbols.google(Symbols,
                    env,
                    return.class = xts ,
                    from = "2007-01-01",
                    to = Sys.Date(),
                    ...)

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


.. TODO
