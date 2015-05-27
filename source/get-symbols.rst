getSymbols
==========

描述
    Functions to load and manage Symbols in specified environment. Used by specifyModel to retrieve
    symbols specified in first step of modelling procedure. Not a true S3 method, but methods for
    different data sources follow an S3-like naming convention. Additional methods can be added by
    simply adhering to the convention.

    当前src方法可用的有：yahoo, google, MySQL, FRED, csv, RData, 和 oanda.

    缺省地，数据静默加载而无需用户赋值.

用法
::

    getSymbols(Symbols = NULL,
        env = parent.frame(),
        reload.Symbols = FALSE,
        verbose = FALSE,
        warnings = TRUE,
        src = "yahoo",
        symbol.lookup = TRUE,
        auto.assign = getOption( getSymbols.auto.assign ,TRUE),
        ...)

    loadSymbols(Symbols = NULL,
        env = parent.frame(),
        reload.Symbols = FALSE,
        verbose = FALSE,
        warnings = TRUE,
        src = "yahoo",
        symbol.lookup = TRUE,
        auto.assign = getOption( loadSymbols.auto.assign ,TRUE),
        ...)

    showSymbols(env=parent.frame())

    removeSymbols(Symbols=NULL,env=parent.frame())

    saveSymbols(Symbols = NULL,
        file.path=stop("must specify file.path "),
        env = parent.frame())

参数
    :Symbols:           a character vector specifying the names of each symbol to be loaded
    :env:               where to create objects. Setting env=NULL is equal to auto.assign=FALSE
    :reload.Symbols:    boolean to reload current symbols in specified environment. (FALSE)
    :verbose:           boolean to turn on status of retrieval. (FALSE)
    :warnings:          boolean to turn on warnings. (TRUE)
    :src:               character string specifying sourcing method. (yahoo)
    :symbol.lookup:     retrieve symbol’s sourcing method from external lookup (TRUE)
    :auto.assign:       should results be loaded to env If FALSE, return results instead. As of 0.4-0, this
    :is:                the same as setting env=NULL. Defaults to TRUE
    :file.path:         character string of file location
    :...:               additional parameters

详细
    getSymbols is a wrapper to load data from various sources, local or remote. Data is fetched via one
    of the available getSymbols methods and either saved in the env specified - the parent.frame()
    by default – or returned to the caller. The functionality derives from base::load behavior and
    semantics, i.e. is assigned automatically to a variable in the specified environment without the
    user explicitly assigning the returned data to a variable. The assigned variable name is that of the
    respective Symbols value.
    The previous sentence’s point warrants repeating - getSymbols is called for its side effects, and by
    defaultdoes not return the data object loaded. The data is ‘loaded’ silently by the function into the
    environment specified.
    If automatic assignment is not desired, env may be set to NULL, or auto.assign set to FALSE.
    The early versions of getSymbols assigned each object into the user’s .GlobalEnv by name (pre 2009
    up to versions less than 0.4-0). This behavior is now supported by manually setting env=.GlobalEnv.
    As of version 0.4-0, the environment is set to parent.frame(), which preserved the user workspace
    when called within another scope.
    This behavior is expect to change for getSymbols as of 0.5-0, and all results will instead be explicitly
    returned to the caller unless a auto.assign is set to TRUE. Many thanks to Kurt Hornik and Achim
    Zeileis for suggesting this change, and further thanks to Dirk Eddelbuettel for encouraging the move
    to a more functional default by 0.5-0.
    Using auto.assign=TRUE, the variable chosen is an R-legal name derived from the symbol being
    loaded. It is possible, using setSymbolLookup to specify an alternate name if the default is not
    desired. See that function for details.
    If auto.assign=FALSE or env=NULL (as of 0.4-0) the data will be returned from the call, and will
    require the user to assign the results himself. Note that only one symbol at a time may be requested
    when auto assignment is disabled.
    Most, if not all, documentation and functionality related to model construction and testing in quant-
    mod assumes that auto.assign remains set to TRUE and env is a valid environment object for the
    calls related to those functions.
    Upon completion a list of loaded symbols is stored in the specified environment under the name
    .getSymbols.
    Objects loaded by getSymbols with auto.assign=TRUE can be viewed with showSymbols and re-
    moved by a call to removeSymbols. Additional data loading “methods” can be created simply
    by following the S3-like naming convention where getSymbols.NAME is used for your function
    NAME. See getSymbols source code.
    setDefaults(getSymbols) can be used to specify defaults for getSymbols arguments. setDefaults(getSymbols.MySQL)
    may be used for arguments specific to getSymbols.MySQL, etc.
    The “sourcing” of data is managed internally through a complex lookup procedure. If symbol.lookup
    is TRUE (the default), a check is made if any symbol has had its source specified by setSymbolLookup.
    If not set, the process continues by checking to see if src has been specified by the user in the
    function call. If not, any src defined with setDefaults(getSymbols,src=) is used.
    Finally, if none of the other source rules apply the default getSymbols src method is used (‘ya-
    hoo’).

返回值
    Called for its side-effect with env set to a valid environment and auto.assign=TRUE, getSymbols
    will load into the specified env one object for each Symbol specified, with class defined by return.class.
    Presently this may be ts, its, zoo, xts, or timeSeries.
    If env=NULL or auto.assign=FALSE an object of type return.class will be returned.

备注
    As of version 0.4-0, the default env value is now parent.frame(). In interactive use this should
    provide the same functionality as the previous version.
    While it is possible to load symbols as classes other than zoo, quantmod requires most, if not all,
    data to be of class zoo or inherited from zoo - e.g. xts. The additional methods are meant mainly
    to be of use for those using the functionality outside of the quantmod workflow.

另见
    getModelData specifyModel setSymbolLookup getSymbols.csv getSymbols.RData

    getSymbols.oanda getSymbols.yahoo getSymbols.google getSymbols.FRED getFX getMetals

范例
::

    ## Not run:
    setSymbolLookup(QQQ= yahoo ,SPY= google )

    # loads QQQQ from yahoo (set with setSymbolLookup)
    # loads SPY from MySQL (set with setSymbolLookup)
    getSymbols(c( QQQ , SPY ))

    # loads Ford market data from yahoo (the formal default)
    getSymbols( F )

    # loads symbol from MySQL database (set with setDefaults)
    getSymbols( DIA , verbose=TRUE, src= MySQL )

    # loads Ford as time series class ts
    getSymbols( F ,src= yahoo ,return.class= ts )

    # load into a new environment
    data.env <- new.env()
    getSymbols("YHOO", env=data.env)
    ls.str(data.env)

    # constrain to local scope
    try(local( {
        getSymbols("AAPL") # or getSymbols("AAPL", env=environment())
        str(AAPL)
    }))
    exists("AAPL") # FALSE

    # assign into an attached environment
    attach(NULL, name="DATA.ENV")
    getSymbols("AAPL", env=as.environment("DATA.ENV"))
    ls("DATA.ENV")
    detach("DATA.ENV")

    # directly return to caller
    str( getSymbols("AAPL", env=NULL) )
    str( getSymbols("AAPL", auto.assign=FALSE)) # same

    ## End(Not run)


.. TODO
