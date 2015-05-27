fittedModel
===========

描述
    从用buildModel构建的quantmod对象中抽取和替换拟合模型.
    所有通过buildModel调用时指定的方法拟合的对象可被抽取出来用于进一步分析.

用法
::

    fittedModel(object)

    ## S3 method for class 'quantmod'
    formula(x, ...)

    ## S3 method for class 'quantmod'
    plot(x, ...)

    ## S3 method for class 'quantmod'
    coefficients(object, ...)

    ## S3 method for class 'quantmod'
    coef(object, ...)

    ## S3 method for class 'quantmod'
    residuals(object, ...)

    ## S3 method for class 'quantmod'
    resid(object, ...)

    ## S3 method for class 'quantmod'
    fitted.values(object, ...)

    ## S3 method for class 'quantmod'
    fitted(object, ...)
    ## S3 method for class 'quantmod'
    anova(object, ...)

    ## S3 method for class 'quantmod'
    logLik(object, ...)

    ## S3 method for class
    vcov(object, ...)

参数
    :object:    一个 quantmod 对象
    :x:         一个合适的（suitable）对象
    :...:       附加参数

详细
    最常用于建模过程中的最终拟合对象，通常利用quantmod包以外的工具做进一步分析.

    大多数应用到拟合对象的方法也可用于quantmod的父对象。目前，可以直接调用以下S3方法应用在构建模型上，就像直接应用在拟合对象上。
    查看 *用法* 部分.

    添加一个拟合模型到一个对象上也是可能的。这对于将探索式的规则集合应用到交易方式上，或者手工微调已有拟合模型是有价值.

返回值
    返回一个和调用buildModel中指定方法所返回对象相匹配的对象

备注
    替换函数 ``fittedModel<-`` 是高度试验性的，将来版本中可能不会再有了。

    添加的拟合模型必须使用和quantmod对象数据集中出现的名字一样的名字。

另见
    quantmod buildModel

范例
::

    ## Not run:

    x <- specifyModel(Next(OpCl(DIA)) ~ OpCl(VIX))
    x.lm <- buildModel(x,method= lm ,training.per=c( 2001-01-01 , 2001-04-01 ))
    fittedModel(x.lm)
    coef(fittedModel(x.lm))
    coef(x.lm) # same
    vcov(fittedModel(x.lm))
    vcov(x.lm) # same

    ## End(Not run)

