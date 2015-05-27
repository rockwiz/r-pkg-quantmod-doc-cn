getSplits
=========

描述
    从雅虎财经下载股票分拆（拆股）数据

用法
::

    getSplits(Symbol,
            from = "1970-01-01",
            to = Sys.Date(),
            env = parent.frame(),
            src = "yahoo",
            auto.assign = FALSE,
            auto.update = FALSE,
            verbose = FALSE, ...)

参数
    :Symbol:        雅虎股票代码
    :from:          CCYY-MM-DD格式开始日期
    :to:            CCYY-MM-DD格式结束日期
    :env:           在何处创建对象
    :src:           数据源（目前仅雅虎可用）
    :auto.assign:   结果是否加载到环境
    :auto.update:   自动添加拆股到数据对象
    :verbose:       显示抓取状态
    :...:           当前未用

详细

    Eventually destined to be a wrapper function along the lines of getSymbols to different sources -
    this currently only support Yahoo data.

返回值
    If auto.assign is TRUE, the symbol will be written to the environment specified in env with a .div appended to the name.

    If auto.update is TRUE and the object is of class xts, the dividends will be included as an attribute of the original object and be reassigned to the environment specified by env.

    All other cases will return the split data as an xts object. NA is returned if there is no split data.

备注
    该函数还处于非常初级阶段 - 将来很可能会做重大改动

参考
    雅虎财经 http://finance.yahoo.com

另见
    getSymbols getDividends

范例
::

    ## Not run:

    getSymbols("MSFT")
    getSplits("MSFT")
    getSplits(MSFT)

    ## End(Not run)


