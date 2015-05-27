getSymbols.FRED
===============

描述
    R access to over 11,000 data series accessible via the St. Louis Federal Reserve Bank’s FRED
    system.
    Downloads Symbols to specified env from ‘research.stlouisfed.org’. This method is not to be called
    directly, instead a call to getSymbols(Symbols,src= FRED ) will in turn call this method. It is
    documented for the sole purpose of highlighting the arguments accepted, and to serve as a guide to
    creating additional getSymbols ‘methods’.

用法
::

    getSymbols.FRED(Symbols,
                    env,
                    return.class = "xts",
                    ...)

参数
    :Symbols:       a character vector specifying the names of each symbol to be loaded
    :env:           where to create objects. (.GlobalEnv)
    :return.class:  class of returned object
    :...:           additional parameters

详细
    Meant to be called internally by getSymbols (see also).
    One of many methods for loading data for use with quantmod. Essentially a simple wrapper to the
    underlying FRED data download site.
    Naming conventions must follow those as seen on the Federal Reserve Bank of St Louis’s website
    for FRED. A lookup facility will hopefully be incorporated into quantmod in the near future.

返回值
    A call to getSymbols.FRED will load into the specified environment one object for each Symbol
    specified, with class defined by return.class. Presently this may be ts, its, zoo, xts, or
    timeSeries.

参考
    St. Louis Fed: Economic Data - FRED http://research.stlouisfed.org/fred2/

另见
    getSymbols setSymbolLookup

范例
::

    ## Not run:
    # All 3 getSymbols calls return the same
    # CPI data to the global environment
    # The last example is what NOT to do!

    ## Method #1
    getSymbols( CPIAUCNS ,src= FRED )

    ## Method #2
    setDefaults(getSymbols,src= FRED )

    # OR
    setSymbolLookup(CPIAUCNS= FRED )
    getSymbols( CPIAUCNS )

    ## End(Not run)


