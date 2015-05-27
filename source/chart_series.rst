chart_Series
============

描述
    这些是quantmod中chartSeries新版本的试验性函数。接口、行为以及功能都会改变

用法
::

    chart_Series(x,
                name = deparse(substitute(x)),
                type = "candlesticks",
                subset = "",
                TA = "",
                pars = chart_pars(),
                theme = chart_theme(),
                clev = 0,
                ...)

参数
    :x:         时序对象
    :name:      图形名字
    :type:      one of:
    :subset:    一个ISO8601风格指示日期范围的字符串
    :TA:        一个逗号分隔的TA调用字符串
    :pars:      图形参数
    :theme:     图形主题
    :clev:      颜色层次（试验性），指示亮度级别，0为最暗的颜色
    :...:       额外参数

详细
    这些函数完成后将会退回到原来的chartSeries命名习惯。

返回值
    引起图形意外结果

备注
    高度试验性，使用要谨慎
