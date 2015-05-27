addExpiry
=========

描述
    Apply options or futures expiration vertical bars to current chart.

用法
::

    addExpiry(type = "options", lty = "dotted")

参数
    :type:      options or futures expiration
    :lty:       type of lines to draw

说明
    查看quantmod包中的options.expiry和futures.expiry获取细节内容和局限

返回值
    合约到期线将绘制在合适的日期上，同时静默返回一个chobTA对象

另见
    `addTA`_

范例
::

    ## Not run:
    addExpiry()
    ## End(Not run)

