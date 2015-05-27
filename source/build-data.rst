buildData
=========

描述
    Create one data object from multiple sources, applying transformations via standard R formula mechanism.

用法
::

    buildData(formula, na.rm = TRUE, return.class = "zoo")

参数
    :formula:       an object of class formula (or one that can be coerced to that class): a symbolic description of the desired output data object, with the dependent side corresponding to first column, and the independent parameters of the formula assigned to the remaining columns.
    :na.rm:         drop rows with missing values?
    :return.class:  one of "zoo","data.frame","ts","its","timeSeries"

详细
    Makes available for use outside the quantmod workflow a dataset of appropriately transformed
    variables, using the same mechanism underlying specifyModel. Offers the ability to apply trans-
    formations to raw data using a common formula mechanism, without having to explicitly merge
    different data objects.

    Interally calls specifyModel followed by modelData, with the returned object being coerced to the
    desired ’return.class’ if possible, otherwise returns a zoo object.

    See getSymbols and specifyModel for more information regarding proper usage.

返回值
    An object of class return.class.

另见
    `getSymbols`_ `specifyModel`_ `modelData`_

范例
::

    ## Not run:

    buildData(Next(OpCl(DIA)) ~ Lag(TBILL) + I(Lag(OpHi(DIA))^2))
    buildData(Next(OpCl(DIA)) ~ Lag(TBILL), na.rm=FALSE)
    buildData(Next(OpCl(DIA)) ~ Lag(TBILL), na.rm=FALSE, return.class="ts")

    ## End(Not run)


