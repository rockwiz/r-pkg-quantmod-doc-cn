getFX
=====

描述
    从oanda下载汇率和金属交易价格

用法
::

    getFX(Currencies,
        from = Sys.Date() - 499,
        to = Sys.Date(),
        env = parent.frame(),
        verbose = FALSE,
        warning = TRUE,
        auto.assign = TRUE, ...)

参数
    :Currencies:        ‘CUR/CUR’ 形式的货币对
    :from:              ISO CCYY-MM-DD 格式的开始日期
    :to:                ISO CCYY-MM-DD 格式的结束日期
    :env:               要加载到哪个环境
    :verbose:           输出详细信息
    :warning:           输出警告信息
    :auto.assign:       自动加载
    :...:               传递给getSymbols.oanda方法的附加参数

详细
    getSymbols(x,src=oanda)的封装函数. 查看getSymbols和getSymbols.oanda获取更多细节内容.

返回值
    The results of the call will be the data will be assigned automatically to the environment specified
    (parent by default). Additionally a vector of downloaded symbol names will be returned.

    查看getSymbols和getSymbols.oanda获取更多细节内容.

参考
    Oanda.com http://www.oanda.com

另见
    getSymbols getSymbols.oanda

范例
::

    ## Not run:

    getFX("USD/JPY")
    getFX("EUR/USD",from="2005-01-01")

    ## End(Not run)


