OHLC.Transformations
====================

描述

    从合适的OHLC对象中抽取（转换）数据。列名字必须包含完整描述 - “Open”、“High”、“Low”、“Close”、“Volume”或“Adjusted” -
    尽管也可能包含另外的字符。这是大多数getSymbols调用返回的对象的缺省值。
    对于包含Op、Hi、Lo和Cl组合（例如，ClCl(x)）的函数，将应用一个周期的转换。

    例如，要返回开盘收盘价之比，调用OpCl(x)。如果期望多期，需要调用Delt。

    seriesLo和seriesHi分别返回给定序列的最低值和最高值。seriesAccel、seriesDecel、seriesIncr和seriesDecr
    分别返回指示该序列正加速、减速、增长和下跌的罗辑向量。它由提供NA填充和适当再索引的diff函数管理。这些使交易规则易于阅读：
    HLC抽取最高、最低和收盘价列；OHLC抽取开盘、最高、最低和收盘价列。

    这些函数只是加快模型规格参数的处理速度。所有列也可以通过标准R方法抽取。

    赋值目前还不可行。

用法
::

    Op(x)
    Hi(x)
    Lo(x)
    Cl(x)
    Vo(x)
    Ad(x)
    seriesHi(x)
    seriesLo(x)
    seriesIncr(x, thresh=0, diff.=1L)
    seriesDecr(x, thresh=0, diff.=1L)
    OpCl(x)
    ClCl(x)
    HiCl(x)
    LoCl(x)
    LoHi(x)
    OpHi(x)
    OpLo(x)
    OpOp(x)
    HLC(x)
    OHLC(x)
    OHLCV(x)

参数
    :x:         一个包含要抽取数据的列的数据对象
    :thresh:    噪音阈值 (seriesIncr/seriesDecr)
    :diff:      差值 (seriesIncr/seriesDecr)

详细
    在内部，程序代码用grep来定位合适的列。因此需要用匹配描述部分要求的列名字输入，尽管精确的命名惯例不是那么重要。

返回值
    返回一个和原来序列类相同的对象，如果符合并/或可能，也附上合适的列名字。唯一例外的是quantmod.OHLC对象，它将作为zoo对象返回，
    并调用也许返回数值而非原对象类型的seriesLo和seriesHi函数。

另见
    `specifyModel`_

范例
::

    ## Not run:

    getSymbols( IBM ,src= yahoo )
    Ad(IBM)
    Cl(IBM)
    ClCl(IBM)
    seriesHi(IBM)
    seriesHi(Lo(IBM))
    removeSymbols( IBM )

    ## End(Not run)


