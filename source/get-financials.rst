getFinancials
=============

描述
    从谷歌财经下载损益表、资产负债表和现金流量表

用法
::

    getFinancials(Symbol, env = parent.frame(), src = "google",
                auto.assign = TRUE, ...)

    viewFinancials(x, type=c( BS , IS , CF ), period=c( A , Q ),
                subset = NULL)

参数
    :Symbol:        一个或多个谷歌代码，字符向量或逗号分隔的字符串
    :env:           在何处创建对象
    :src:           当前未用
    :auto.assign:   结果是否要加载到环境中
    :...:           当前未用
    :x:             一个 financials 类的对象
    :type:          要查看报表的类型
    :period:        要查看报表的期间
    :subset:        ‘xts’ 风格的子集字符串

详细
    A utility to download financial statements for publically traded companies. The data is directly
    from Google finance. All use of the data is under there Terms of Service, available at http://www.google.com/accounts/TOS.
    Individual statements can be accessed using standard R list extraction tools, or by using viewFinancials.

    viewFinancials allows for the use of date subsetting as available in the xts package, as well as the
    specification of the type of statement to view. BS for balance sheet, IS for income statement, and
    CF for cash flow statement. The period argument is used to identify which statements to view - (A)
    for annual and (Q) for quarterly.

返回值
    组织在一个financials类列表中的六个单独矩阵：

    :IS: 包括季度（Q）和年度（A）损益表的列表
    :BS: 包括季度（Q）和年度（A）资产负债表的列表
    :CF: 包括季度（Q）和年度（A）现金流量表的列表

备注
    所有免费数据，风险自担

参考
    谷歌财经 http://finance.google.com/finance

范例
::

    ## Not run:

    getFinancials( JAVA ) # returns JAVA.f to "env"
    getFin( AAPL )        # returns AAPL.f to "env"

    viewFin(JAVA.f, "IS", "Q")  # Quarterly Income Statement
    viewFin(AAPL.f, "CF", "A")  # Annual Cash Flows

    str(AAPL.f)

    ## End(Not run)


