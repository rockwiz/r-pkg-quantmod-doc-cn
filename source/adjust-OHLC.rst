adjustOHLC
==========

描述
    根据股票分割和分红情况调整一个OHLC对象的所有列 [#]_

用法
::

    adjustOHLC(x,
            adjust = c("split","dividend"),
            use.Adjusted = FALSE,
            ratio = NULL,
            symbol.name = deparse(substitute(x)))

参数
    :x:             一个OHLC对象
    :adjust:        根据分割、分红或两者（默认）调整
    :use.Adjusted:  使用雅虎数据中的‘Adjusted’列
    :ratio:         调整比例，不进行内部计算
    :symbol.name:   x的名字和所调整股票的代码不一样时使用

详细
    该函数根据股票分割和分红信息计算调整后的开、高、低、收价格。

    有三种方法计算新的OHLC对象价格。

    缺省地，将调用getSplits和getDividends来获取相应的信息，这些函数将遵循quantmod分发 [#]_ 所用的“点规范”把相关任务指派给相应的定制方法。

    查看getSymbols获知扩展quantmod相关的信息。该信息传递给TTR包中的adjRatios函数，所得计算结果用于调整观察到的历史价格，
    这是调整一个序列最精确的方法。

    第二种方法仅用于包含调整列的标准雅虎数据。

    最后一种方法是直接给函数传递一个比例参数。

    所有方法都按以下方式处理：

    首先获取原始收盘价的调整比例，再乘以相应列和原始收盘价之间的差。然后加到调整后的收盘价列上得到“调整后”的开盘、最高和最低价。

    如果不需要调整，该函数返回没有改变的原始数据。

返回值
    一个原来的类的对象，加上根据分割和分红调整后的价格列

警告
    使用 use.Adjusted = TRUE 后的精度低于采用实际分割和分红信息的方法。这是由于雅虎调整列精度只有2位。好处是这样可以离线运行，
    对于较短序列或调整较少序列而言，这种精度上的损失比较小。

    所得精度损失是行观测之间的，因为计算基于日内值。
    （译者注：一行数据，即一天的开、高、低、收价格，相当于一个观测样本。每天调整后的开、高、低价格是根据当天的调整后收盘价计算而来）

参考
    雅虎财经 http://finance.yahoo.com

另见
    `getSymbols.yahoo`_ `getSplits`_ `getDividends`_

范例
::

    ## Not run:

    getSymbols("AAPL", from="1990-01-01", src="yahoo")
    head(AAPL)
    head(AAPL.a <- adjustOHLC(AAPL))
    head(AAPL.uA <- adjustOHLC(AAPL, use.Adjusted=TRUE))
    # intrada adjustments are precise across all methods
    # an example with Open to Close (OpCl)
    head(cbind(OpCl(AAPL),OpCl(AAPL.a),OpCl(AAPL.uA)))
    # Close to Close changes ma lose precision
    head(cbind(ClCl(AAPL),ClCl(AAPL.a),ClCl(AAPL.uA)))

    ## End(Not run)

