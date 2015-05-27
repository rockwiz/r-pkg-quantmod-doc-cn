has.OHLC
========

描述
    A set of functions to check for appropriate OHLC and HLC column names within a data object, as
    well as the availability and position of those columns.

用法
::

    is.OHLC(x)
    has.OHLC(x, which = FALSE)

    is.OHLCV(x)
    has.OHLCV(x, which = FALSE)

    is.HLC(x)
    has.HLC(x, which = FALSE)
    has.Op(x, which = FALSE)
    has.Hi(x, which = FALSE)
    has.Lo(x, which = FALSE)
    has.Cl(x, which = FALSE)
    has.Vo(x, which = FALSE)
    has.Ad(x, which = FALSE)

    is.BBO(x)
    is.TBBO(x)

    has.Ask(x, which = FALSE)
    has.Bid(x, which = FALSE)
    has.Price(x, which = FALSE)
    has.Qty(x, which = FALSE)
    has.Trade(x, which = FALSE)

参数
    :x:         数据对象
    :which:     disply position of match

详细
    Mostly used internally by quantmod, they can be useful for checking whether an object can be
    used in OHLC requiring functions like Op, OpCl, etc.
    Columns names must contain the full description of data, that is, Open, High, Low, Close, Volume
    or Adjusted. Abbreviations will return FALSE (or NA when which=TRUE). See quantmod.OHLC for
    details of quantmod naming conventions.
    is.OHLC (and is.HLC, similarly) will only return TRUE is there are columns for Open, High, Low
    and Close. Additional columns will not affect the value.

返回值
    A logical value indicating success or failure by default.

    If which=TRUE, a numeric value representing the column position will be returned.

    is.OHLC and is.HLC return a single value of TRUE or FALSE.

参考
    see ADX in TTR written by Josh Ulrich

另见
    quantmod.OHLC OHLC.Transformations

范例
::

    ## Not run:

    getSymbols("YHOO")
    is.OHLC(YHOO)
    has.OHLC(YHOO)
    has.Ad(YHOO)

    ## End(Not run)

.. TODO
