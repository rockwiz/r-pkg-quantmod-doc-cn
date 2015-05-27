getMetals
=========

描述
    从oanda下载每天的金属价格

用法
::

    getMetals(Metals,
            from = Sys.Date() - 500,
            to = Sys.Date(),
            base.currency="USD",
            env = parent.frame(),
            verbose = FALSE,
            warning = TRUE,
            auto.assign = TRUE, ...)

参数
    :Metals:            metals expressed in common name or symbol form
    :from:              start date expressed in ISO CCYY-MM-DD format
    :to:                end date expressed in ISO CCYY-MM-DD format
    :base.currency:     which currency should the price be in
    :env:               which environment should they be loaded into
    :verbose:           be verbose
    :warning:           show warnings
    :auto.assign:       use auto.assign
    :...:               additional parameters to be passed to getSymbols.oanda method

详细
    A convenience wrapper to getSymbols(x,src= oanda ).
    The most useful aspect of getMetals is the ablity to specify the Metals in terms of underlying 3 char-
    acter symbol or by name (e.g. XAU (gold) , XAG (silver), XPD (palladium), or XPT (platinum)).
    There are unique aspects of any continuously traded commodity, and it is recommended that the
    user visit http://www.oanda.com for details on specific pricing issues.

    查看getSymbols和getSymbols.oanda获取更多细节内容.

返回值
    Data will be assigned automatically to the environment specified (parent by default). If auto.assign
    is set to FALSE, the data from a single metal request will simply be returned from the function call.
    If auto.assign is used (the default) a vector of downloaded symbol names will be returned.
    See getSymbols and getSymbols.oanda for more detail.

参考
    Oanda.com http://www.oanda.com

另见
    `getSymbols`_ `getSymbols.oanda`_

范例
::

    ## Not run:

    my.model <- specifyModel(Next(OpCl(QQQQ)) ~ Lag(Cl(NDX),0:5))
    getModelData(my.model)

    ## End(Not run)

