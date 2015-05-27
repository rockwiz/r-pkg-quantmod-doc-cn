periodReturn
============

描述
    给定一个价格集合，返回周期性收益

用法
::

    periodReturn(x,
                period= monthly ,
                subset=NULL,
                type= arithmetic ,
                leading=TRUE,
                ...)

    dailyReturn(x, subset=NULL, type= arithmetic ,
                leading=TRUE, ...)

    weeklyReturn(x, subset=NULL, type= arithmetic ,
                leading=TRUE, ...)

    monthlyReturn(x, subset=NULL, type= arithmetic ,
                leading=TRUE, ...)

    quarterlyReturn(x, subset=NULL, type= arithmetic ,
                leading=TRUE, ...)

    annualReturn(x, subset=NULL, type= arithmetic ,
                leading=TRUE, ...)

    yearlyReturn(x, subset=NULL, type= arithmetic ,
                leading=TRUE, ...)

    allReturns(x, subset=NULL, type= arithmetic ,
                leading=TRUE)

参数
    :x:         规定价格对象或一个OHLC类型对象
    :period:    指示时间期间的字符串。有效条目包括：
                ‘daily’, ‘weekly’, ‘monthly’, ‘quarterly’, ‘yearly’.
                所有都可以从下述的包装函数中访问。默认是月度收益（和monthlyReturn一样）
    :subset:    一个xts/ISO8601风格子集字符串
    :type:      收益类型：算数（离散）或对数（连续）
    :leading:   是否返回不完整的前导期收益
    :...:       单独传递给to.period

详细
    periodReturn是以下封装函数的基本函数：

        | allReturns: 计算所有有效周期的收益
        | dailyReturn: 计算日收益
        | weeklyReturn: 计算周收益
        | monthlyReturn: 计算月收益
        | quarterlyReturn: 计算季度收益
        | annualReturn: 计算年收益

返回值
    返回一个原先传入的类的对象，如果可用，有可能附带月度和季度收益指数转换成yearmon和yearqtr类异常。
    这可以通过用传递给to.period函数...参数中的indexAt参数来覆盖。

    缺省地，如果subset是NULL，则使用整个数据集。

备注
    如果xts包支持，尝试将结果序列转换成原来的类。目前，继承ts类的对象返回成xts对象。
    这会使结果视觉效果更有感染力、信息量更丰富。如果期望，所有xts对象可以通过as.ts转换成ts类。

    返回对象的首行和末行将有直到最后一天的周期收益，也就是该周/月/季/年的到期收益，即使start/end不是该周期的起始/结束。
    前导期计算可以通过设置leading=FALSE予以忽略。

另见
    getSymbols

范例
::

    ## Not run:

    getSymbols( QQQQ ,src= yahoo )
    allReturns(QQQQ) # returns all periods

    periodReturn(QQQQ,period= yearly ,subset= 2003:: ) # returns years 2003 to present
    periodReturn(QQQQ,period= yearly ,subset= 2003 ) # returns year 2003

    rm(QQQQ)

    ## End(Not run)


