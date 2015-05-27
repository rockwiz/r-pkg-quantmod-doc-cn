getSymbols.csv
==============

描述
    Downloads Symbols to specified env from local comma seperated file. This method is not to be
    called directly, instead a call to getSymbols(Symbols,src= csv ) will in turn call this method. It
    is documented for the sole purpose of highlighting the arguments accepted, and to serve as a guide
    to creating additional getSymbols ‘methods’.

用法
::

    getSymbols.csv(Symbols,
                env,
                dir="",
                return.class = "xts",
                extension="csv",
                ...)

参数
:Symbols:       a character vector specifying the names of each symbol to be loaded
:env:           where to create objects. (.GlobalEnv)
:dir:           directory of csv file
:return.class:  class of returned object
:extension:     extension of csv file
:...:           附加参数

详细
    Meant to be called internally by getSymbols (see also).
    One of a few currently defined methods for loading data for use with quantmod. Essentially a
    simple wrapper to the underlying R read.csv.

返回值
    调用getSymbols.csv将把每个指定证券代码一个根据return.class指定的类，目前支持ts, its, zoo, xts, 或 timeSeries，的对象加载到指定环境
    A call to getSymbols.csv will load into the specified environment one object for each Symbol speci-
    fied, with class defined by return.class. Presently this may be ts, its, zoo, xts, or timeSeries.

备注
    This has yet to be tested on a windows platform. It should work though file seperators may be an issue.

另见
    getSymbols read.csv setSymbolLookup

范例
::

    ## Not run:
    # All 3 getSymbols calls return the same
    # MSFT to the global environment

    ## Method #1
    getSymbols( MSFT ,src= csv )

    ## Method #2
    setDefaults(getSymbols,src= csv )

    # OR
    setSymbolLookup(MSFT= csv )
    getSymbols( MSFT )

    ## End(Not run)


