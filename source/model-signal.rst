modelSignal
===========

描述
    从quantmodResults对象中抽取模型信号对象作为zoo类的对象

用法
::

    modelSignal(x)

参数
    :x: 一个quantmodResults类的对象

详细
    用于调用tradeModel后抽取给定quantmod模型的生成信号。最终用户通常不需要调用，除非他在手工处理交易结果。

返回值
    由单一日期索引的zoo对象

另见
    tradeModel
