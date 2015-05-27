getOptionChain
==============

描述
    Function to download option chain data from data providers.

用法
::

    getOptionChain(Symbols, Exp = NULL, src="yahoo", ...)

参数
    :Symbols:   The name of the underlying symbol
    :Exp:       One or more expiration dates, or NULL. If Exp is missing, the default is to only
    :return:    the front month contract.
    :src:       Source of data. Currently only ‘yahoo’ is provided
    :...:       additional parameters

详细
    This function is a wrapper to data-provider specific APIs. By default the data is sourced from yahoo.

返回值
    A named list containing two data.frames, one for calls and one for puts. If more than one expiration
    was requested, this two-element list will be contained within list of length length(Exp). Each
    element of this list will be named with the expiration month and year (for Yahoo sourced data).
    If Exp is set to NULL, all expirations will be returned. Not explicitly setting will only return the front
    month.

参考
    雅虎财经 http://finance.yahoo.com

范例
::

    ## Not run:

    AAPL.OPT <- getOptionChain("AAPL")
    AAPL.OPTS <- getOptionChain("AAPL", NULL)

    ## End(Not run)


