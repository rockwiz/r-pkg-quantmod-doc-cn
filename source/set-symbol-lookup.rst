setSymbolLookup
===============

描述
    在R会话（session）中创建和管理证券代码缺省值查询表，供getSymbols调用时使用

用法
::

    setSymbolLookup(...)
    getSymbolLookup(Symbols=NULL)
    unsetSymbolLookup(Symbols,confirm=TRUE)
    saveSymbolLookup(file,dir="")
    loadSymbolLookup(file,dir="")

参数
    :...:       证券代码缺省值name=value对
    :Symbols:   代码名字
    :confirm:   删除查询表前警示
    :file:      文件名
    :dir:       文件目录

详细
    使用这些函数可以让用户在加载每个证券时为其指定一套缺省参数。

    可以随意给每个证券代码指定getSymbols方法中有效的数据来源（如yahoo, MySQL, csv）。查阅getSymbols了解哪些方法可用，以及如何新加方法。

    给setSymbolLookup的参数列表就是与期望的缺省数据源相匹配的没有引号的代码名字，或者代码特定参数。

    例如，表示Sun Microsystems (JAVA)的股票数据应该从雅虎财经下载，
    只要调用setSymbolLookup(JAVA=yahoo)或setSymbolLookup(JAVA=list(src=yahoo)。

    也可以以每个证券代码为基础对其指定额外可能和数据源相关的查询细节。包括替代的命名习惯（对一些网站有用。比如在雅虎，非交易证券以^字符开头。
    在那种情况下，需要指定setSymbolLookup(DJI=list(name="^DJI",src="yahoo"))），针对数据库源提供类似dbname和password这样的参数。
    查阅和数据源相关的特定getSymbols函数获取每个具体实现的详细信息。

    如果一个命名列表传递给函数而没有将该列表命名为参数，该列表的名字就被推测为要加入到当前证券代码列表中的证券代码的名字。

    给当前列表所做的所有改变将保留到会话结束。要一直使用相同的缺省值，需要用适当的参数从启动文件（例如，.Rprofile）中调用setSymbolLookup，
    或者用saveSymbolLookup和loadSymbolLookup保存和恢复查询表。

    删除指定代码的缺省值，给该代码赋值NULL即可。

返回值
    该函数通过调用options(getSymbols.sources=...)改变每个指定证券的选项值

备注
    改变 **不** 会跨会话保持，因为表缺省地是存储在会话选项中。
    以后这个可能会变从而使管理过程更容易，目前为止设计目标还是尽量减少一个典型会话中产生的混乱。

另见
    `getSymbols`_ `options,`_

范例
::

    setSymbolLookup(QQQQ= yahoo ,DIA= MySQL )
    getSymbolLookup( QQQQ )
    getSymbolLookup(c( QQQQ , DIA ))

    ## Not run:
    ## Will download QQQQ from yahoo
    ## and load DIA from MySQL

    getSymbols(c( QQQQ , DIA ))

    ## End(Not run)

    ## Use something like this to always retrieve
    ## from the same source

    .First <- function() {
        require(quantmod,quietly=TRUE)
        quantmod::setSymbolLookup(JAVA="MySQL")
    }

    ## OR

    saveSymbolLookup()
    loadSymbolLookup()


