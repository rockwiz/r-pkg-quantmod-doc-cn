addVo
=====

描述
    Add Volume of a series, if available, to the current chart. This is the default TA argument for all charting functions.

用法
::

    addVo(log.scale=FALSE)

参数
    :log.scale: use log-scale for volume

详细
   Add volume bars to current chart if data object contains appropriate volume column.

   log.scale will transform the series via standard R graphics mechanisms.

返回值
    Volume will be draw in a new window on the current chart. A chobTA object will be returned silently.

参考
    see ADX in TTR written by Josh Ulrich

另见
    `addTA`_

范例
::

    ## Not run:
    addVo()
    ## End(Not run)

