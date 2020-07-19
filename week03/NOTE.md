学习笔记
#语句Statement
    1.简单语句
    2.组合语句
    3.声明

##语句运行结果记录Completion Record
        解析，完成之后是怎么完成的  用数据结构存储语句完成的结果：是否返回？返回了什么
    组成：【type】
          [value]
          [target]
    简单语句
        1.表达式语句：eXpressionStatrment
        2.空语句：EmptyStatement    单独的一个;
        3.DebuggerStatement:Debugger语句后面加;  用法：出发一个DEBUGGER断点 上线前都会移除
        4.ThrowStatement
        5.ContinueStatement
        6.BreakStatement
        7.ReturnStatement

    复合语句
        1. BlockStatement  {}语句
        2.IfStatement
        3.SwitchStatement 不建议再JS中使用
        4.IterationStatement FOR  DO 等循环
        5.WithStatement Witch打开对象把属性都放作用域去，可以节约空间和记忆成本  不确定很高  拒绝使用
        6.LabelledStatement   相当于给语句取名 再语句前加labelled
        7.TryStatement    三段结构  try(不能省略{}这个是try语块提供，不是8.BlockStatement提供所以不能省略) catch finely

##声明
    var声明的会被归于语句
    声明类型
        1.FunctionDeclarration
        2.GeneratorDeclatation
        3.AsyncFunctionDeclaration      异步声明
        4.AsynGeneratorDeclaration      异步的产生器声明
        5.VariableStatement   变量声明
        6.ClassDeclaration
        7.LexicalDeclaration

    声明
        class const let 声明前使用会报错    有一个预处理的作用 这是新加的特性
##预处理pre-process
    提前找到var声明
    const a 变成局部变量    没有影响到外面的a

    作用域
        var作用域在他咋的函数体，因为预处理机制的原因
        corst作用域在他所在的{}



#表达式
##运算符运算优先级
    JS用表达式来表达运算运算优先级
        */会形成更低一级的语法结构  +-会形成让你更高一级的语法结构

    1.Member优先级最高 典型代表：a.b  是一个分级的名称 不完全是一个运算符
        Member:
            a.b a[b]支持运行时的字符串
        foo `string` 与mamber优先同一级
        new.target:
        new Foo()  不带（）的new new Foo 优先级更低

        运行时
            引用类型，称作标准中的类型

        函数调用 Call Expressions
             Example:new a()[b'] new了一个a对象然后访问了一个B对象

    2.左手右手运算（Left Handside & Right Handside）
        left handside 才能跟圆括号
            不能放左边的： Update
                1.a++
                2.a--
                3.--a
                4.++a
    3.unary(单目运算符)
        delete a.b
        void foo() void运算符是把后面的都变成Underfind
        typeof a
         +a
         -a
         ~a  位运算 吧整数按位取法 不是整数强制转化为整数
         !a
         await a 会对后续语法造成影响
    右结合运算符
         ** ：3**2**3：先运算2*3 再处理3**后面的
            
    4.Multiplicative  必须是number字符
    5.Additive  
    6.Shift   移位运算  Relationship    比较运算
    
    7.Equality双等比较  Bitwise双 与或非

    8.Logical与或非运算
    9.Conditional 唯一一个三目运算符  ？： 一定 意义上可以替换if else

        
##类型转换(Type Convertion)
    最复杂的类型转换'=='
        类型相同的就能比较，类型不同的就转换为Number类型进行比较    建议使用'==='或者做完类型转换之后再比较
    位运算先转成Number类型后再转为整数类型
###拆箱转换UnBoxing
    把Object类型转换为基本类型
    ToPremitive 发生再表达式第一的方方面面 eg:加运算
         三个方法会影响到ToPremitive方法
         ToString vs valueOf 
            加法会优先调用valueOf
            O作为属性名优先调用ToString
         Symbol.toPrimitive

    Symbol无法直接NEW，要先用Object再包装  eg:new Object(Symbol("a"))  值：Symbol("a")

#结构化

##JS执行力度
    1.宏任务      传给JS引擎的
        then后面的代码 异步执行     MicroTask(Job)
    2.微任务      在JS引擎内运行的
    3.函数调用

##函数调用
    函数调用本身也会形成一个stack 栈

    Exection Context Stack 执行上下文栈

    LexicalEnvironment
        所有执行的东西都保存在里面
    VariableEnvironment  
        仅仅用来用于处理var声明，
    多数时候这两个是重合的

##Environment Record
    平时生产是大量使用和产生的是Declarative Environment Records 不是抽象类 可以初始化

##Function-Closure 每个函数都会产生一个函数闭包

##Realm
    规定了在一个JS引擎的实例里面他所有的内置对象会被放到一个Realm中

OC代码
ER概念
查看JS标准
realm
LexicalEnvironment
VariableEnvironment
数据可视化框架    推荐蚂蚁G6
