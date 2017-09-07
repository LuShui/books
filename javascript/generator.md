Generator
    含义：一种异步编程解决方案
    形式：，Generator 函数是一个普通函数，但是有两个特征。
        一是，function关键字与函数名之间有一个星号；
        二是，函数体内部使用yield表达式，定义不同的内部状态
        function 后面的星号没有规定写在哪里，所以以下4种方式都是等效的
            function* base(){}
            function * base(){}
            function *base(){}
            function*base(){}
    function* base() {
        yield 'base1';
        yield 'base2';
        yield 'base3';
        return 'end';
    }
    调用方式：调用结束后继续调用返回undefined
        let b = base();
        console.log(b.next());//{value: "base1", done: false}
        console.log(b.next());//{value: "base2", done: false}
        console.log(b.next());//{value: "base3", done: false}
        console.log(b.next());//{value: "end", done: true}
        console.log(b.next());//{value: "undefined", done: true}
 调用方式看起来像断点调试的形式



 yield关键字
    在函数中，yield类似于暂停操作，即运行到这里就暂停。
    只有当调用next()方法才进行下一步，知道遇到下一个yield。
    若未遇到yield则一直运行到最后。直到return结束。
    如果没有return，则最后会返回undefined。



next()方法
    function * NumberMath(x) {
        let a = 2 * (yield x);
        let b =  yield (a+10);
        return (a+b+x);
    }
    let num = NumberMath(10);
        console.log(num.next());//{value: 10, done: false}
        console.log(num.next());//{value: NaN, done: false}
        console.log(num.next());//{value: NaN, done: true}
        console.log(num.next());//{value: undefined, done: true}

    let num = NumberMath(10);
        console.log(num.next());//{value: 10, done: false}
        console.log(num.next(10));//{value: 30, done: false}
        console.log(num.next(10));//{value: 40, done: true}
        console.log(num.next());//{value: undefined, done: true}
        所以得出结论，next的参数讲替代yield表达式。


 yield*表达式，用来在一个 Generator 函数里面执行另一个 Generator 函数
    function* foo() {
        yield 'e';
        yield 'l';
        yield 'l';
    }
    function* bar() {
        yield 'h';
        yield *foo();
        yield 'o';
    }
    for (let v of bar()){
        console.log(v);//h e l l o
     }