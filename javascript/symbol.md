1、Symbol 概述
        表示独一无二的值。它是 JavaScript 语言的第七种数据类型，
        前六种是：undefined、null、布尔值（Boolean）、字符串（String）、数值（Number）、对象（Object）
        Symbol 值不能与其他类型的值进行运算，会报错

    2、作为属性名的 Symbol
        由于每一个 Symbol 值都是不相等的，这意味着 Symbol 值可以作为标识符，用于对象的属性名，就能保证不会出现同名的属性。
        这对于一个对象由多个模块构成的情况非常有用，能防止某一个键被不小心改写或覆盖
            var mySymbol = Symbol();
            // 第一种写法
                var a = {};
                a[mySymbol] = 'Hello!';
            // 第二种写法
                var a = {
                    [mySymbol]: 'Hello!'
                };
            // 第三种写法
                var a = {};
                Object.defineProperty(a, mySymbol, { value: 'Hello!' });
            // 以上写法都得到同样结果
                a[mySymbol] // "Hello!"

        Symbol 值作为对象属性名时，不能用点运算符（使用点运算符将其看成字符串了）
            var mySymbol = Symbol();
            var a = {};
            a.mySymbol = 'Hello!';
            a[mySymbol] // undefined
            a['mySymbol'] // "Hello!"

     4、属性名的遍历
        Symbol 作为属性名，该属性不会出现在for...in、for...of循环中，
        也不会被Object.keys()、Object.getOwnPropertyNames()、JSON.stringify()返回。
        但是，它也不是私有属性，有一个Object.getOwnPropertySymbols方法，可以获取指定对象的所有 Symbol 属性名。
        Object.getOwnPropertySymbols方法返回一个数组，成员是当前对象的所有用作属性名的 Symbol 值。


     5、Symbol.for()，Symbol.keyFor()
        Symbol.for方法接受一个字符串作为参数，
            然后搜索有没有以该参数作为名称的Symbol值。
            如果有，就返回这个Symbol值，
            否则就新建并返回一个以该字符串为名称的Symbol值
        Symbol.for()与Symbol()这两种写法，都会生成新的Symbol。
        它们的区别是，
            前者会被登记在全局环境中供搜索，后者不会。
            Symbol.for()不会每次调用就返回一个新的 Symbol 类型的值，
            而是会先检查给定的key是否已经存在，
            如果不存在才会新建一个值。
            比如，如果你调用Symbol.for("cat")30次，每次都会返回同一个 Symbol 值，
            但是调用Symbol("cat")30次，会返回30个不同的Symbol值

        Symbol.keyFor   方法返回一个已登记的 Symbol 类型值的key
            参数为一个Symbol对象
            未登记的Symbol值，返回undefined