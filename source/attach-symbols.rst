attachSymbols
=============

描述
    把一个需求数据库（延迟加载）到一个新工作环境

用法
::

    attachSymbols(DB = DDB_Yahoo(),
                pos = 2,
                prefix = NULL,
                postfix = NULL,
                mem.cache = TRUE,
                file.cache = !mem.cache,
                cache.dir = tempdir())

    flushSymbols(DB = DDB_Yahoo())

参数
    :DB:            一个DDB数据库对象
    :pos:           附加DB的搜索路径位置
    :prefix:        所有代码前缀字符
    :postfix:       所有代码后缀字符
    :mem.cache:     对象是否要在内存里缓存
    :file.cache:    对象是否要缓存到磁盘
    :cache.dir:     file.cache=TRUE 时的目录

详细
    无需显式调用加载函数而允许访问远端对象的试验性函数。

    attachSymbols需要一个DDB对象来定义数据从哪里来，以及哪些证券代码要按需加载。
    attachSymbols调用DDB提到的方法，缺省情况下是DDB_Yahoo，查阅该函数以了解雅虎实现的细节信息。

    单个方法利用getSymbols来加载数据，因此需要相应的getSymbols方法。

    在内部，attachSymbols利用quantmod不对外的create.bindings方法动态创建DDB对象中列出的每个代码的有效绑定。

    反过来，create.bindings利用两个R方法之一创建所需名字的绑定，它依赖于请求的缓存方法。


    An experimental function to allow access to remote objects without requiring explicit calls to a
    loading function.
    attachSymbols requires a DDB object to define where the data is to come from, as well as what
    symbols are loaded on-demand.
    attachSymbols calls the method referred to by the DDB object. In the default case this is DDB_Yahoo.
    See this function for specific details about the Yahoo implementation.

    The individual methods make use of getSymbols to load the data. This requires a corresponding
    getSymbols method.

    Internally, attachSymbols makes use of quantmod’s unexported create.bindings to dynamically cre-
    ate active bindings to each symbol listed in the DDB object.

    In turn, create.bindings uses one of two R methods to create the binding to the names required. This
    depends on the cache method requested.

    Immediately after a call to attachSymbols, a new environment is attached that contains the names
    of objects yet to be loaded. This is similar to the lazy-load mechanism in R, though extended to be
    both more general and easier to use.

    It is important to note that no data is loaded at this stage. What occurs instead is that these sym-
    bols now have active bindings using either delayedAssign (mem.cache) or makeActiveBinding
    (file.cache).
    During all future requests for the object(s) in question, the binding will be used to determine how
    this data is loaded into R. mem.cache will simply load the data from its corresponding source (as
    defined by the DDB object) and leave it in the environment specified in the original call. The effect
    of this is to allow lazy-loading of data from a variety of external sources (Yahoo in the default case).
    Once loaded, these are cached in R’s memory. Nothing further differentiates these from standard
    variables. This also means that the environment will grow as more symbols are loaded.
    If the file.cache option is set, the data is loaded from its source the first time the symbol is refer-
    enced. The difference is that the data is then written to a temporary file and maintained there. Data
    is loaded and subsequently removed upon each request for the object. See makeActiveBinding for
    details of how this occurs at the R level.
    A primary advantage of using the file.cache option is the ability to maintain hundreds or thousands
    of objects in your current session without using memory, or explicitly loading and removing. The
    main downside of this approach is the that data must be loaded from disk each time, with the
    corresponding (if generally negligible) overhead of file access.

备注
    该函数是新引入的，在不久的未来，所有方面都可能改变

另见
    delayedAssign makeActiveBinding

范例
::

    ## Not run:

    attachSymbols()
    SBUX
    QQQQ
    ls()

    ## End(Not run)

