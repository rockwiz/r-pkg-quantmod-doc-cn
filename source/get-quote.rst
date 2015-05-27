getQuote
========

描述
    从指定数据源抓取股票数据。目前只能从雅虎财经获取，但以后会扩展到更多数据源

用法
::

    getQuote(Symbols, src = "yahoo", what, ...)

    standardQuote(src="yahoo")

    yahooQF(names)

    yahooQuote.EOD

参数
    :Symbols:   代码字符串，以逗号分隔
    :src:       数据源（quantmod只实现了雅虎）
    :what:      要获取哪些数据
    :names:     要获取哪个数据
    :...:       当前未用currently unused

返回值
    A maximum of 200 symbols may be requested per call to Yahoo!, and all requested will be returned
    in one data.frame object. If more that 200 symbols are requested, multiple 200 symbol calls will be
    made and the results will be returned as one data object.

    getQuote returns a data frame with rows matching the number of Symbols requested, and the
    columns matching the requested columns.

    The what argument allows for specific data to be requested. For getQuote.yahoo, the value of what
    should be a quoteFormat object like that returned by standardQuote which contains Yahoo!’s
    formatting string. If not provided, the A list and interactive selection tool can be seen with yahooQF.
    standardQuote currently only applied to Yahoo! data, and returns an object of class quoteFormat,
    for use within the getQuote function.

    yahooQuote.EOD is a constant quoteFormat object for OHLCV data.

参考
    雅虎财经 http://finance.yahoo.com gummy-stuff.org http://www.gummy-stuff.org/Yahoo-data.htm

另见
    getSymbols

范例
::

    yahooQuote.EOD

    ## Not run:

    getQuote("AAPL")
    getQuote("QQQQ;SPY;^VXN",what=yahooQF(c("Bid","Ask")))
    standardQuote()
    yahooQF()

    ## End(Not run)

