getModelData
============

描述
    用最新数据更新指定或构建的模型

用法
::

    getModelData(x, na.rm = TRUE)

参数
    :x:         An object of class quantmod
    :na.rm:     Boolean. Remove NA values. Defaults to TRUE

详细
    Primarily used within specify model calls, getModelData is used to retrieve the appropriate un-
    derlying variables, and apply model specified transformations automatically. It can be used to also
    update a current model in memory with the most recent data.

返回值
    Returns object of class quantmod.OHLC

参考

另见
    getSymbols specifyModel buildModel modelData

范例
::

    ## Not run:

    my.model <- specifyModel(Next(OpCl(QQQQ)) ~ Lag(Cl(NDX),0:5))
    getModelData(my.model)

    ## End(Not run)

