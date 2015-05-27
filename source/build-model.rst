buildModel
==========

描述
    Construct and attach a fitted model of type method to quantmod object.

用法
::

    buildModel(x, method, training.per, ...)

参数
    :x:             An object of class quantmod created with specifyModel or an R formula
    :training.per:  character vector representing dates in ISO 8601 format “CCYY-MM-DD” or “CCYY-MM-DD HH:MM:SS” of length 2
    :method:        A character string naming the fitting method. See details section for available methods, and how to create new methods.
    :...:           Additional arguments to method call

详细
    目前可用的方法包括：

    lm, glm, loess, step, ppr, rpart[rpart], tree[tree], randomForest[randomForest], mars[mda], poly-
    mars[polspline], lars[lars], rq[quantreg], lqs[MASS], rlm[MASS], svm[e1071], and nnet[nnet].

    The training.per should match the undelying date format of the time-series data used in mod-
    elling. Any other style may not return what you expect.

    Additional methods wrappers can be created to allow for modelling using custom functions. The
    only requirements are for a wrapper function to be constructed taking parameters quantmod, training.data,
    and . . . . The function must return the fitted model object and have a predict method available. It
    is possible to add predict methods if non exist by adding an S3 method for predictModel. The
    buildModel.skeleton function can be used for new methods.

返回值
    An object of class quantmod with fitted model attached

参考
    See buildModel.skeleton for information on adding additional methods

另见
    `specifyModel`_ `tradeModel`_

范例
::

    ## Not run:

    getSymbols( QQQQ ,src= yahoo )
    q.model = specifyModel(Next(OpCl(QQQQ)) ~ Lag(OpHi(QQQQ),0:3))
    buildModel(q.model,method= lm ,training.per=c( 2006-08-01 , 2006-09-30 ))

    ## End(Not run)

