quantmod-class
==============

描述
    quantmod类的对象帮助管理quantmod包中的建模过程。通过调用specifyModel自动创建，所承载的信息将被各式各样的访问函数和方法使用。

类对象
    对象可通过以new("quantmod", ...)的形式调用来创建

    通常对象创建是调用specifyModel的结果

槽位（slot）
    :model.id: Object of class "character" ~~
    :model.spec: Object of class "formula" ~~
    :model.formula: Object of class "formula" ~~
    :model.target: Object of class "character" ~~
    :model.inputs: Object of class "character" ~~
    :build.inputs: Object of class "character" ~~
    :symbols: Object of class "character" ~~
    :product: Object of class "character" ~~
    :price.levels: Object of class "zoo" ~~
    :training.data: Object of class "Date" ~~
    :build.date: Object of class "Date" ~~
    :fitted.model: Object of class "ANY" ~~
    :model.data: Object of class "zoo" ~~
    :quantmod.version: Object of class "numeric" ~~

范例
::

    showClass("quantmod")


