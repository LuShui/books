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
    next 可以传递参数用于替代yield表达式

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
            所以得出结论，next的参数将替代yield表达式。

        yield 关键字的运算规则
            从右到左运算，优先级别为2
                除了 展开运算符 ，逗号的优先级小于它之外，其他的运算符优先级都大于它
                yield* 的运算优先级也是2



Generator.prototype.throw()
    可以在函数体外抛出错误，然后在 Generator 函数体内捕获，
    如果Generator 函数内部没有部署try...catch代码块，那么throw方法抛出的错误，将被外部try...catch代码块捕获，
    如果 Generator 函数内部和外部，都没有部署try...catch代码块，那么程序将报错，直接中断执行
    还接受一个参数，该参数会被catch语句接收，建议抛出Error对象的实例

    只要 Generator 函数内部部署了try...catch代码块，那么遍历器的throw方法抛出的错误，不影响下一次遍历，
    而且捕获一次错误后会执行一次yield

    注：区分Generator.prototype.throw() 和 throw
        前者是Generator对象上的一个方法，抛出的错误会被Generator内部捕获
        后者是全局对象window对象的方法，只会被外部的catch捕获



Generator.prototype.return() 
    返回给定的值，并且终结遍历 Generator 函数
    Generator 函数内部有try...finally代码块，那么return方法会推迟到finally代码块执行完再执行



next()、throw()、return() 的共同点
    next()是将yield表达式替换成一个值。
    throw()是将yield表达式替换成一个throw语句。
    return()是将yield表达式替换成一个return语句。



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



作为对象属性的Generator函数
    let obj = {
        * generatir(){

        }
    }
    let obj = {
        generatir: function* (){

        }
    }
    以上两个表达式等价



Generator 函数的this
    Generator 函数总是返回一个遍历器，ES6 规定这个遍历器是 Generator 函数的实例，也继承了 Generator 函数的prototype对象上的方法

    可以通过call(),apply()等方法为Generator函数绑定this
    function* gen() {
      this.a = 1;
      yield this.b = 2;
      yield this.c = 3;
    }

    function F() {
      return gen.apply(gen.prototype);
    }

    var f = new F();

    for (let value of f){
        console.log(value);
    }    