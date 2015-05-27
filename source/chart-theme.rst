chartTheme
==========

描述
    在chartSeries中创建一个chart.theme对象来管理期望的图形颜色

用法
::

    chartTheme(theme = "black", ...)

参数
    :theme: 基本主题的名字
    :...:   用来修改的name=value对

详细
    作为chartSeries函数家族的参数使用，chartTheme允许在运行时修改预先指定的图形主题。
    用户能够就地修改预制主题，或复制主题到新变量用于以后的绘图调用。

    在内部，一个chart.theme就是一个按图形部件组织的值的列表，除此之外，没有什么其它特别的。

    这样做的主要目的就是便于运行时做些小的修改，以及为大的改动提供模板。

    通过chartTheme为TA调用设置样式参数需要用户传递name=value对，其中一个name包含所谈到的TA调用。查看范例以获取帮助。

    目前可以用适当的值来修改的部件：

        :fg.colforeground:      color
        :bg.colbackground:      color
        :grid.colgrid:          color
        :borderborder:          color
        :minor.tickminor:       tickmark color
        :major.tickmajor:       tickmark color
        :up.colup:              bar/candle color
        :dn.coldown:            bar/candle color
        :up.up.colup:           after up bar/candle color
        :up.dn.colup:           after down bar/candle color
        :dn.dn.coldown:         after down bar/candle color
        :dn.up.coldown:         after up bar/candle color
        :up.borderup:           bar/candle border color
        :dn.borderdown:         bar/candle border color
        :up.up.borderup:        after up bar/candle border color
        :up.dn.borderup:        after down bar/candle border color
        :dn.dn.borderdown:      after down bar/candle border color
        :dn.up.borderdown:      after up bar/candle border color

返回值
    一个chart.theme对象

另见
    chartSeries

范例
::

    chartTheme()
    chartTheme( white )
    chartTheme( white ,up.col= blue ,dn.col= red )

    # A TA example
    chartTheme(addRSI.col= red )
    str(chartTheme())

