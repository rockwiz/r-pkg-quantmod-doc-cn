chartSeries
===========

描述
    为给定时序类对象创建标准财务图表的画图工具。用来作为未来额外技术分析的基本函数。
    可能的图形风格包括：蜡烛图、火柴图（一根蜡烛）、柱图和线图。图形可以有白色或黑色背景。

    reChart允许动态改变图形，而无需重新指定全部图形参数。

用法
::

    chartSeries(x,
            type = c("auto", "candlesticks", "matchsticks", "bars","line"),
            subset = NULL,
            show.grid = TRUE,
            name = NULL,
            time.scale = NULL,
            log.scale = FALSE,
            TA = addVo() ,
            TAsep= ; ,
            line.type = "l",
            bar.type = "ohlc",
            theme = chartTheme("black"),
            layout = NA,
            major.ticks= auto , minor.ticks=TRUE,
            yrange=NULL,
            plot=TRUE,
            up.col,dn.col,color.vol = TRUE, multi.col = FALSE,
            ...)

    reChart(type = c("auto", "candlesticks", "matchsticks", "bars","line"),
            subset = NULL,
            show.grid = TRUE,
            name = NULL,
            time.scale = NULL,
            line.type = "l",
            bar.type = "ohlc",
            theme = chartTheme("black"),
            major.ticks= auto , minor.ticks=TRUE,
            yrange=NULL,
            up.col,dn.col,color.vol = TRUE, multi.col = FALSE,
            ...)

参数
    :x:             一个OHLC对象
    :type:          图形风格（样式）
    :subset:        xts类型日期子集参数
    :show.grid:     显示价格网格线？
    :name:          图形名称
    :time.scale:    时间尺度是什么？自动推测（不连续）
    :log.scale:     y轴使用对数刻度？
    :TA:            一个技术指标和参数的向量或字符串
    :TAsep:         TA字符串的分隔符
    :line.type:     线型
    :bar.type:      柱状图类型 - ohlc 还是 hlc
    :theme:         一个chart.theme对象
    :layout:        如果为NULL， 忽略内部布局
    :major.ticks:   坐标轴主刻度画在哪里
    :minor.ticks:   坐标轴次刻度画在哪里
    :yrange:        覆盖Y轴刻度
    :plot:          是否画出图形（参考：返回值）
    :up.col:        上涨的柱/蜡烛颜色
    :dn.col:        下跌的柱/蜡烛颜色
    :color.vol:     成交量是否着色
    :multi.col:     四色蜡烛图案
    :...:           额外参数

详细
    目前显示金融应用中标准样式的OHLC图形，或在没有传递OHLC数据时绘制线型图。用于有明确时序属性的对象。

    线图以收盘价创建，或取自时间序列的单个列。

    subset参数用于指定时间序列中要显示的特定区域。基本序列保持完好以便TA函数可以使用全部数据集。
    另外，也可以使用从first和last函数中借用的句法。例如，‘last 4 months’（译者注：最后四个月）。

    TA允许包括多种样式的图形叠加和技术指标。addTA有完整的列表。默认的TA参数是addVo() - 如果可用，就在要绘制的图形上添加成交量。

    theme需要一个通过调用chartTheme创建的chart.theme类的对象。该函数用于修改所得图形的外观。参考chart.theme获知细节。

    line.type和bar.type允许根据个人喜好对图形进行微调。

    multi.col实现了一个颜色编码方案用于一些绘图应用，遵循以下规则：

        * grey => Op[t] < Cl[t] and Op[t] < Cl[t-1]
        * white => Op[t] < Cl[t] and Op[t] > Cl[t-1]
        * red => Op[t] > Cl[t] and Op[t] < Cl[t-1]
        * black => Op[t] > Cl[t] and Op[t] > Cl[t-1]

    reChart从原来的chart调用中获取任意数量的参数，然后用更新后的参数重新绘制图形。
    有一点要注意：如果期望多色柱型图/蜡烛图，那么需要重新指定主题参数。
    另外，目前不能改变TA参数，这个必须通过addTA/dropTA/swapTA/moveTA命令完成。

返回值
    返回一个刻度适宜并加上成交量（如果可用）的标准图形。如果plot=FALSE，将返回一个chob对象。

备注
    图形的大多数细节都可以微调，尽管函数在给坐标轴定刻度和写标签方面做得相当不错了。

    当前实现维持了一个完成任何特定图形的操作记录，它用于在添加新指标时重新创建原图。调用listTA可得一个已执行的TA操作的列表。
    该列表可赋值给一个变量，然后在新的chart调用时用来重新创建一套技术指标。也可以通过调用setTA强制以后所有图形都使用同样的指标。

另见
    `getSymbols`_ `addTA`_ `setTA`_ `chartTheme`_

范例
::

    ## Not run:

    getSymbols("YHOO")
    chartSeries(YHOO)
    chartSeries(YHOO, subset= last 4 months )
    chartSeries(YHOO, subset= 2007::2008-01 )
    chartSeries(YHOO,theme=chartTheme( white ))
    chartSeries(YHOO,TA=NULL)                   # no volume
    chartSeries(YHOO,TA=c(addVo(),addBBands())) # add volume and Bollinger Bands from TTR

    addMACD()                                   # add MACD indicator to current chart

    setTA()

    chartSeries(YHOO)                           # draws chart again, this time will all indicators present

    ## End(Not run)


