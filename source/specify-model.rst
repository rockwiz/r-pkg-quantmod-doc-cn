specifyModel
============

描述
    为紧随其后的buildModel调用创建一个可重用模型规范。创建一个quantmod类对象，该对象随后被不同建模方法和参数重用。
    没有指定数据框，因为数据潜在从多个环境中获取，且调用getSymbols。

用法
::

    specifyModel(formula, na.rm=TRUE)

参数
    :formula: 一个formula（或能强制转换为该类的）类对象：要拟合的模型的符号描述，下面 **详细** 部分给出了模型规范的细节
    :na.rm:   删除所有不完整行

详细
    模型通过标准公式机制指定。

    由于金融模型可能包含各式各样的金融和经济指标，这些指标在来源、频率和/或类等方面各不相同，
    一个单一的指定数据源的机制包括在specifyModel调用中。参阅getModelData获知它如何处理工作的细节。

    目前，模型公式支持quantmod.OHLC、zoo、ts和its类的对象。

    所有证券首先从全局环境中获取，没有继承。如果一个对象在全局环境中没有找到，它就通过getSymbols函数被添加到要装载对象的列表中。
    getSymbols通过setDefaults和setSymbolLookup指定位置获取每个证券代码。

    在内部，所有数据被强制转换为zoo、data.frame或numeric类

返回值
    返回一个quantmod对象。用modelData抽取全部数据设为zoo对象

备注
    可以通过简单地指定对象符号，在公式里包含任何支持的序列。参阅 *Details* 获知目前支持的类的列表。

    用getSymbols.skeleton来创建额外的获取数据方法，例如，从私有数据格式或目前还未实现的数据源（Bloomberg, Oracle）。

    作为增加额外功能的例子，参考getSymbols.MySQL和getSymbols.yahoo

另见
    getModelData getSymbols buildModel tradeModel formula setSymbolLookup

范例
::

    ## Not run:
    # if QQQQ is not in the Global environment, an attempt will be made
    # to retrieve it from the source specified with getSymbols.Default

    specifyModel(Next(OpCl(QQQQ)) ~ Lag(OpHi(QQQQ),0:3) + Hi(DIA))

    ## End(Not run)

