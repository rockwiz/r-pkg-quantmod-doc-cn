create.binding
==============

描述
    attachSymbols中为DDB对象中定义的证券代码创建有效绑定的内部函数

用法
::

    create.binding(s,
                lsym,
                rsym,
                gsrc,
                mem.cache = TRUE,
                file.cache = !mem.cache,
                cache.dir = tempdir(),
                envir,...)

参数
    :s:             证券代码名字
    :lsym:          转换为本地名字的函数（合法的R名字）
    :rsym:          转换为远端名字的函数（源名字）
    :gsrc:          对于getSymbols调用中的’src’参数
    :mem.cache:     缓存到内存
    :file.cache:    缓存到磁盘
    :cache.dir:     直接缓存到/从（目录）
    :envir:         工作环境名字（字符）
    :...:           传递给的getSymbols参数

详细
    初始化需求数据库（DDB，demand-database）构造过程中创建绑定的底层函数

返回值
    引起创建有效绑定到证券代码的意外结果

备注
    这是attachSymbols内部使用的代码。用户可以修改它以适应不同的证券代码。上传（upstream）函数无需维持该接口的一致性。

    作为指南或模板使用
