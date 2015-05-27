options.expiry
==============

描述
    返回合约到期日指数。期权（options）是每月的第三个周五，期货（futures）是每个季度最后一个月的第三个周五

用法
::

    options.expiry(x)
    futures.expiry(x)

参数
    :x: 一个按时间索引的zoo对象

详细
    通过addExpiry用于绘图场景，返回值基于以上描述

返回值
    一个指数的数值向量

备注
    目前没有考虑可能会破坏一般规则的节假日情况，另外所有工作只集中在美国权益（equity）和期货（future）市场

另见
    addExpiry

范例
::

    ## Not run:

    getSymbols("AAPL")
    options.expiry(AAPL)
    futures.expiry(AAPL)
    AAPL[options.expiry(AAPL)]

    ## End(Not run)


