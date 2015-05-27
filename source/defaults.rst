Defaults
========

描述
    指定全局缺省值，如果已设定，则替换指定的参数值。允许用户指定与之前所提供值不一样的缺省值，例如，修改表现较差的缺省值，或满足不同偏好

用法
::

    setDefaults(name, ...)
    unsetDefaults(name, confirm = TRUE)
    getDefaults(name = NULL, arg = NULL)
    importDefaults(calling.fun)

参数
    :name:          函数名，加引号或不加引号都可以
    :...:           name=value缺省对
    :confirm:       删除缺省值前提示
    :arg:           获取的值
    :calling.fun:   要作用于其上的函数的名字

详细
    **setDefaults** 提供一个R选项的封装函数，允许用户为函数的形式参数指定name=valu对。只有正式指定的name=value对会被更新。
    数值无需在随后的setDefaults调用中重新指定，因此可以在不重新键入所有以前数值的情况下，一次性给每个函数添加新的缺省值。
    把NULL赋值给任何参数会将该参数从缺省值列表中删除。

    **unsetDefaults** 把 name=value 对从缺省值列表中删除。

    **getDefaults** 提供访问已存储缺省值的手段。单个参数无需引号，多个参数必须在一个字符向量中。

    **importDefaults** 调用importDefaults必须将其置于函数体的首行。它检查用户工作环境中为要调用函数指定的全局缺省值。
    这些缺省值可被用户通过调用setDefaults来指定，并将覆盖任何缺省的形式参数，实际上就是用用户提供的数值替代原始的缺省值。
    任何用户在父函数（也就是包含importDefaults的那个函数）中指定的数值将覆盖全局缺省环境中设定的数值。

返回值
    :setDefaults: 无
    :unsetDefaults: 无
    :getDefaults: 一个和形参一样的环境变量及其缺省值的命名列表，但只返回那些setDefaults为name函数设定的值。
                    不带参数调用getDefaults()返回所有当前（通过setDefaults）设定缺省值的函数的字符向量。

                    这并不意味返回的函数名能够（通过importDefaults）接受缺省值，尽管它们被设置来存储用户缺省值。
                    所有数值可以通过调用getOption(name_of_function.Default)函数查看。
    :importDefaults: 无。用于获得加载所有用户指定的非NULL缺省值到函数当前工作环境所产生的效果，
                    有效地改变传递给父函数调用的缺省值。如同在函数定义中的形式缺省值，importDefaults设定的缺省值优先级低于用户在
                    函数调用时指定的参数值。

备注
    目前setDefaults还不可能用NULL来替换非NULL缺省值，因为处理过程将NULL解释为没有设置，将只使用函数形式上指定的值。
    如果NULL就是所期望的，那么在函数调用时需要将其包括进去。

    任何函数实际调用中包含的参数优先于setDefaults值，以及标准形式函数值。这与目前用户R体验相一致。

    和选项（option）类似，缺省设置不会跨会话（session）保持。目前，不能给...参数传值，只能在原函数定义中形式上指定参数。

    unsetDefaults为指定函数删除选项列表中的所有条目。要删除单个函数缺省值，只需在setDefaults中将该参数名设为NULL。

    当函数实现importDefaults时，如果一个全局缺省值已被设定（也就是非NULL），未命名参数会被忽略。
    如果是这种情况，只要在调用函数中命名该参数即可。

    这也适用于从选项中获取形参数值的函数，因为它以看起来和在函数调用中传值同样的方式给参数赋值。因此如果一个参数传递给函数，
    可推测任何对选项的检查将忽视importDefaults值。

范例
::

    my.fun <- function(x=3)
    {
        importDefaults( my.fun )
        x^2
    }
    my.fun()    # 返回 9
    setDefaults(my.fun, x=10)
    my.fun()    # 返回 100
    my.fun(x=4) # 返回 16
    getDefaults(my.fun)
    formals(my.fun)
    unsetDefaults(my.fun, confirm=FALSE)
    getDefaults(my.fun)
    my.fun()    # 返回 9


