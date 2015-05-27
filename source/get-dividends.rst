getDividends
============

描述
    从雅虎财经下载或下载附加股票分红（股息）数据

用法
::

    getDividends(Symbol,
                from = "1970-01-01",
                to = Sys.Date(),
                env = parent.frame(),
                src = "yahoo",
                auto.assign = FALSE,
                auto.update = FALSE,
                verbose = FALSE, ...)

参数
    :Symbol:        股票代码
    :from:          date from in CCYY-MM-DD format
    :to:            date to in CCYY-MM-DD format
    :env:           where to create object
    :src:           data source (only yahoo is valid at present)
    :auto.assign:   should results be loaded to env
    :auto.update:   automatically add dividend to data object
    :verbose:       display status of retrieval
    :...:           currently unused

详细
    Eventually destined to be a wrapper function along the lines of getSymbols to different sources -
    this currently only support Yahoo data.

返回值
    If auto.assign is TRUE, the symbol will be written to the environment specified in env with a .div
    appended to the name.

    If auto.update is TRUE and the object is of class xts, the dividends will be included as an attribute
    of the original object and be reassigned to the environment specified by env.

    所有其它情况下将返回作为xts对象的分红（股息）数据.

备注
    该函数还非常初级，今后很可能会重大改变

参考
    雅虎财经 http://finance.yahoo.com

另见
    getSymbols

范例
::

    ## Not run:

    getSymbols("MSFT")
    getDividends("MSFT")
    getDividends(MSFT)

    ## End(Not run)


