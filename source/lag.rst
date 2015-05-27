Lag
====

描述
    从数据中创建一个滞后序列，用NA填充

用法
::

    Lag(x, k = 1)

    ## S3 method for class
    Lag(x, k = 1) quantmod.OHLC

    ## S3 method for class
    Lag(x, k = 1) zoo

    ## S3 method for class
    Lag(x, k = 1) data.frame

    ## S3 method for class
    Lag(x, k = 1)

参数
    :x:         要进行滞后运算的序列或向量
    :k:         滞后期数

详细
    Shift series k-periods down, prepending NAs to front of series.

    Specifically designed to handle quantmod.OHLC and zoo series within the quantmod workflow. If no S3 method is found, a call to lag in base is made.

返回值
    The original x prepended with k NAs and missing the trailing k values.

    返回序列维持原始对象的个数

备注
    This function differs from lag by returning the original series modified, as opposed to simply changing the time series properties. It differs from the like named Lag in the Hmisc as it deals primarily with time-series like objects.

    It is important to realize that if there is no applicable method for Lag, the value returned will be from lag in base. That is, coerced to ts if necessary, and subsequently shifted.

另见
    lag

范例
::

    Stock.Close <- c(102.12,102.62,100.12,103.00,103.87,103.12,105.12)
    Close.Dates <- as.Date(c(10660,10661,10662,10665,10666,10667,10668),origin="1970-01-01")
    Stock.Close <- zoo(Stock.Close,Close.Dates)

    Lag(Stock.Close) #lag by 1 period
    Lag(Stock.Close,k=1) #same
    Lag(Stock.Close,k=1:3) #lag 1,2 and 3 periods


