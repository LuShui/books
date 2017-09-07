  1、默认参数
        example
            function log(b,a = 'hello') {
                console.log(a,b);
             };  log('es6'); //es6 htllo
        参数变量是默认声明的，所以不能用let或const再次声明
        如果参数默认值是变量，那么参数就不是传值的，而是每次都重新计算默认值表达式的值
        let x = 10;
        function log(b,a = x) {
            console.log(a+b);
         }
        log(5);//15
        x=20;
        log(5);//25
     函数的 length 属性
        length属性的含义是，该函数预期传入的参数个数。某个参数指定默认值以后，预期传入的参数个数就不包括这个参数了
        通常情况下，定义了默认值的参数，应该是函数的尾参数。
        如果设置了默认值的参数不是尾参数，那么length属性也不再计入后面的参数了
        (function (a = 0, b, c) {}).length // 0
        (function (a, b = 1, c) {}).length // 1
     作用域
        一旦设置了参数的默认值，函数进行声明初始化时，参数会形成一个单独的作用域（context）。
        等到初始化结束，这个作用域就会消失。这种语法行为，在不设置参数默认值时，是不会出现的。


     2、 rest 参数(将一系列的值快速的转化为一个数组)
        example
        function rest(...values) {
            let sum = 0;
            values.forEach(function (item) {
                sum += item
            });
            console.log(sum);
        };
        rest(1,2,3,4,5,6,7,8);//36

        function rest(arr,...values) {
            let sum = 0;
            values.forEach(function (item) {
                sum += item
            });
            console.log(sum);
        };
        var arr = [1,2,3,4,5,6,8];
        rest(arr,1,2,3,4,5,6,7,8);//36

        rest 参数中的变量代表一个数组，所以数组特有的方法都可以用于这个变量（所以用了forEach）
        rest 参数之后不能再有其他参数（即只能是最后一个参数），否则会报错
        函数的length属性，不包括 rest 参数


     3、拓展运算符
        扩展运算符（spread）是三个点（...）。它好比 rest 参数的逆运算，将一个数组转为用逗号分隔的参数序列
            console.log(...[1, 2, 3]) //1 2 3

     4、严格模式(ES5严格模式)
        1. 变量必须使用var声明，杜绝不小心将本地变量声明成一个全局变量
        2. 对超出权限的操作显示报错，不再做静默失败处理
        3. 禁止删除变量和对象中不可删除的属性，显示报错
        4. 禁止对象属性重名
        5. 禁止函数参数重名
        6. 禁止使用八进制数字
        7. 禁止使用with语句
        8. 强制为eval创建新作用域
        9. 禁止对eval和arguments做非法操作
        10. arguments不再追踪参数变化
        11. 禁止使用arguments.callee
        12. 禁止this指向全局
        13. 禁止使用function直接引用caller和arguments
        14. 函数必须声明在整个脚本或函数层面
        15. 新增一些保留字


     5、name 属性
     函数的name属性，返回该函数的函数名。


     6、箭头函数
     ES6允许使用“箭头”（=>）定义函数
     var f = v=>v;
        function f(v) {
          return v;
        }

     如果箭头函数不需要参数或需要多个参数，就使用一个圆括号代表参数部分。
     var f = () => 2*2;  //不需要参数
        function f() {
            return 2*2;
        }
     let f = (a,b)=>a+b;    //  多个参数
        function f(a,b) {
            return a+b;
        }
     如果箭头函数的代码块部分多于一条语句，就要使用大括号将它们括起来
     let f = (a,b)=>{
        let aa = a*a;
        let bb = b*b;
        console.log( aa+bb);
    };
        function f(a,b) {
            let aa = a*a;
            let bb = b*b;
            console.log( aa+bb);
        }
     let f = (a,b)=>{
        let aa = a*a;
        let bb = b*b;
        return {
            "aa":aa,
            "bb":bb
        };
    };
     如果箭头函数直接返回一个对象，必须在对象外面加上括号
     let f = (name,age)=>({
        'name':name,
        'age':age
    });
     箭头函数有几个使用注意点。
        （1）函数体内的this对象，就是定义时所在的对象，而不是使用时所在的对象。
                (若在全局定义，就是指向window对象，若定义在某个函数，则指向那个函数
                    所以箭头函数没有自己的this对象，故也没有arguments、super对象，
                    同时不能用call()、apply()、bind()这些方法去改变this的指向)
        （2）不可以当作构造函数，也就是说，不可以使用new命令，否则会抛出一个错误。
        （3）不可以使用arguments对象，该对象在函数体内不存在。如果要用，可以用Rest参数代替。
        （4）不可以使用yield命令，因此箭头函数不能用作Generator函数。



     7、绑定 this
        该语法还是ES7的一个提案，但是Babel转码器已经支持(babel可以使用构建工具进行配置)
        函数绑定运算符是并排的两个双冒号（::），
        双冒号左边是一个对象，右边是一个函数。
        该运算符会自动将左边的对象，作为上下文环境（即this对象），绑定到右边的函数上面

     8、尾调用
        某个函数的最后一步是调用另一个函数
        尾调用不一定出现在函数尾部，只要是最后一步操作即可
        尾递归         函数调用自身，称为递归。如果尾调用自身，就称为尾递归

     9、函数参数的尾逗号
        ES2017 允许函数的最后一个参数有尾逗号