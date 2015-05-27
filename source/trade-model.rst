tradeModel
==========

描述
    拟合quantmod对象的模拟交易。给定一个拟合模型，tradeModel计算给定历史时期生成的信号，然后运用特定trade.rule来计算和返回
    tradeLog对象。然后可调用额外的方法来评估模型策略的性能。

用法
::

    tradeModel(x,
            signal.threshold = c(0, 0),
            leverage = 1,
            return.model = TRUE,
            plot.model = FALSE,
            trade.dates = NULL,
            exclude.training = TRUE,
            ret.type = c("weeks", "months", "quarters", "years"),
            ...)

参数
    :x:                 一个来自buildModel的quantmod对象
    :signal.threshold:  一个描述交易发生前上下阈值的数值向量
    :leverage:          要采用的杠杆总数 - 目前是常量
    :return.model:      要返回全部模型？
    :plot.model:        绘制该模型？
    :trade.dates:       指定交易间隔 - 默认为全数据集
    :exclude.training:  将训练期排除在外？
    :ret.type:          周期收益表
    :...:               基本建模函数所需的额外参数

详细
    还处于高度试验性和变化中。目标是把一个从buildModel中新构造的模型应用到新数据集以考察该模型的交易性能。

    目前所有参数都是非常基本的。比较近的改变项包括允许一个trade.rule参数为给定信号集建立动态交易规则。
    另外，杠杆和成本的应用将成为最终结构的一部分。

返回值
    一个quantmodResults对象

另见
    specifyModel buildModel

范例
::

    ## Not run:

    m <- specifyModel(Next(OpCl(QQQQ)) ~ Lag(OpHi(QQQQ)))
    m.built <- buildModel(m,method= rpart ,training.per=c( 2007-01-01 , 2007-04-01 ))
    tradeModel(m.built)
    tradeModel(m.built,leverage=2)

    ## End(Not run)


