quantmod.OHLC
=============

描述
    把一个有适当的列的对象强制转换成quantmod.OHLC类。quantmod.OHLC是zoo类的扩展

用法
::

    as.quantmod.OHLC(x,
                    col.names = c("Open", "High",
                    "Low", "Close",
                    "Volume", "Adjusted"),
                    name = NULL, ...)

参数
    :x:         zoo类对象
    :col.names: 列后缀
    :name:      附着到唯一的列后缀的名字，缺省为对象名
    :...:       额外参数（未使用）

详细
    quantmod.OHLC实际上是zoo类对象的重命名，以NAME.Open, NAME.High, ...作为列名字。

返回值
    一个 c(’quantmod.OHLC’,’zoo’) 类的对象

另见
    `OHLC.Transformations`_ `getSymbols`_
