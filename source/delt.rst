Delt
====

描述
    Calculate the k-period percent difference within one series, or between two series. Primarily used to
    calculate the percent change from one period to another of a given series, or to calculate the percent
    difference between two series over the full series.

用法
::

    Delt(x1, x2 = NULL, k = 0, type = c("arithmetic", "log"))

参数
    :x1:        m x 1 vector
    :x2:        m x 1 vector
    :k:         change over k-periods. default k=1 when x2 is NULL.
    :type:      type of difference. log or arithmetic (default).

详细
    When called with only x1, the one period percent change of the series is returned by default. Inter-
    nally this happens by copying x1 to x2. A two period difference would be specified with k=2.
    If called with both x1 and x2, the difference between the two is returned. That is, k=0. A one period
    difference would be specified by k=1. k may also be a vector to calculate more than one period at a
    time. The results will then be an m x length(k)

    Log differences are used by default: :math:`Lag=\log{\frac{x_{2}(t)}{x_{1}(t-k}}`

    Arithmetic differences are calculated: :math:`Lag=\frac{x_{2}(t)-x_{1}(t-k)}{x_{1}(t-k)}`

返回值
    An matrix of length(x1) rows and length(k) columns.

参考
    see ADX in TTR written by Josh Ulrich

另见
    OHLC.Transformations

范例
::

    Stock.Open <- c(102.25,102.87,102.25,100.87,103.44,103.87,103.00)
    Stock.Close <- c(102.12,102.62,100.12,103.00,103.87,103.12,105.12)

    Delt(Stock.Open)        #one period pct. price change
    Delt(Stock.Open,k=1)    #same
    Delt(Stock.Open,type= arithmetic ) #using arithmetic differences

    Delt(Stock.Open,Stock.Close)        #Open to Close pct. change
    Delt(Stock.Open,Stock.Close,k=0:2)  #...for 0,1, and 2 periods


