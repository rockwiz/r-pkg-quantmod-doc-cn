modelData
=========

描述
    从quantmod对象中抽取数据集用于建模。

    specifyModel在随后把各种来源的所有输入合并到一个模型框架的工作阶段（buildModel,tradeModel）创建一个zoo对象。

    modelData返回该对象。

用法
::

    modelData(x, data.window = NULL, exclude.training = FALSE)

参数
    :x:                 一个quantmod对象
    :data.window:       要返回的子集的起止日期的字符向量
    :exclude.training:  去除训练期

详细
    当一个模型被specifyModel创建，它就挂载在返回对象上。该S4类的槽位（slot）之一是model.data。

返回值
    一个包含specifyModel中指定数据所有转换的zoo类对象

另见
    specifyModel getModelData

范例
::

    ## Not run:

    m <- specifyModel(Next(OpCl(SPY)) ~ Cl(SPY) + OpHi(SPY) + Lag(Cl(SPY)))
    modelData(m)

    ## End(Not run)


