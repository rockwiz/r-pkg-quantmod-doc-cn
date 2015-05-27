saveChart
=========

描述
    将所选图表保存为外部文件

用法
::

    saveChart(.type = "pdf", ..., dev = dev.cur())

参数
    :.type: 导出类型。查看 *详细*
    :...:   传递给设备的参数
    :dev:   要导出到哪个设备

详细
    该函数包装R函数pdf, postscript, png, jpeg, and bitmap。.type参数必须指定期望哪个设备驱动。

    如果dev缺失，则使用当前活跃设备。结果是精确（设备限度内）复制所选图表。

    产生的文件的名字取自图表名字，附加适当的扩展名（由.type确定）。指定适当设备file/filename（文件/文件名）将覆盖此名字。

    调用者可以指定对所调用设备有效的任何参数。在内部，尽量匹配所用设备的尺寸来创建输出文件，用户提供的尺寸大小将覆盖内部计算。

返回值
    当前目录（缺省）下一个匹配请求输出类型的文件

备注
    由于该函数用do.call在内部创建新的输出设备，任何利用R惯例的设备都是可作为.type值被接受的。

另见
    pdf png jpeg bitmap postscript

范例
::

    ## Not run:

    getSymbols("AAPL")
    chartSeries(AAPL)
    require(TTR)
    addBBands()
    saveChart( pdf )
    saveChart( pdf , width=13)

    ## End(Not run)


