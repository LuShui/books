Promise
        含义：Promise 是异步编程的一种解决方案，替代es5的回调函数
            promise 对象初始化完成之后就会立即执行
        简单用法
        let promise = new  Promise(function (resolve,reject) {
            setTimeout(()=>resolve('succed'),5000);
        });
        promise.then(function (value) {
            console.log(value)
        },function (error) {
            console.log(error);
        });


     Promise.prototype.then()
        为Promise实例添加状态改变时的回调函数。
        then方法的第一个参数是Resolved状态的回调函数，
        第二个参数（可选）是Rejected状态的回调函数


     Promise.prototype.catch()
        then(null, rejection)的别名，用于指定发生错误时的回调函数