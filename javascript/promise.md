Promise
    含义：Promise 是异步编程的一种解决方案，替代es5的回调函数
          promise 对象初始化完成之后就会立即执行

          特性：
            1、对象的状态不受外界影响。Promise对象代表一个异步操作，有三种状态：pending（进行中）、fulfilled（已成功）和rejected（已失败）
            2、一旦状态改变，就不会再变，任何时候都可以得到这个结果。Promise对象的状态改变，只有两种可能：从pending变为fulfilled和从pending变为rejected。
          缺点：
            1、无法取消Promise，一旦新建它就会立即执行，无法中途取消
            2、如果不设置回调函数，Promise内部抛出的错误，不会反应到外部。
            3、当处于pending状态时，无法得知目前进展到哪一个阶段


    方法或者属性
        Promise.prototype.then() 该方法会返回一个新的promiss对象
            接受两个回调函数作为参数。
            第一个回调函数是Promise对象的状态变为resolved时调用，
            第二个回调函数是Promise对象的状态变为rejected时调用。
            其中，第二个函数是可选的
                new Promise((resolve,reject)=>{
                    setTimeout(()=>{
                        let ret = {
                            'code':1
                        }
                        resolve(ret);
                    },2000);
                }).then((ret)=>{
                    ret['age'] = 25;
                    console.log(ret);
                    return ret;
                }).then((ret)=>{
                    ret['name'] = 'javascript';
                    console.log(ret);
                });


        Promise.prototype.catch() 该方法会返回一个新的promiss对象
            then(null, rejection)的别名，用于指定发生错误时的回调函数
            Promise 对象的错误具有“冒泡”性质，会一直向后传递，直到被捕获为止。也就是说，错误总是会被下一个catch语句捕获


        Promise.all()
            将多个 Promise 实例，包装成一个新的 Promise 实例
            接受一个数组作为参数，数组的成员都是 Promise 实例，如果不是，就会先调用Promise.resolve方法，将参数转为 Promise 实例，再进一步处理
            注意：（参数可以不是数组，但必须具有 Iterator 接口，且返回的每个成员都是 Promise 实例）
            它的状态依赖数组成员中promiss对象的状态，只有所有的promiss对象的状态都为resolve，它的状态才是resolve，
            否则则是reject

        Promise.race()
            将多个Promise实例，包装成一个新的Promise实例
            它的状态取决于第一个改变状态的promiss对象的状态。

        Promise.resolve()
            将现有对象转为Promise对象
            1、参数是一个Promise实例
                如果参数是Promise实例，那么Promise.resolve将不做任何修改、原封不动地返回这个实例

            2、参数是一个thenable对象(thenable对象指的是具有then方法的对象，比如下面这个对象)
                let thens = {
                    then:function(resolve,reject){
                        reject('1234');
                    }
                };
                示例：这个示例会执行catch的回调方法，输出1234
                let promiss = Promise.resolve(thens);
                promiss.then((ret)=>{
                    console.log(ret);
                }).catch((err)=>{
                    console.log(err);
                });

                执行步骤：
                    通过Promise.resolve生成promiss对象后，会立即执行thens中的then方法。

            3、参数不是具有then方法的对象，或根本就不是对象
                示例：这个示例会执行resolve回调方法，输出php
                let promiss = Promise.resolve('php');
                promiss.then((ret)=>{
                    console.log(ret);
                }).catch((err)=>{
                    console.log(err);
                });

                执行步骤：
                    通过Promise.resolve生成promiss对象后，默认的状态为resolve，会立即执行resolve回调

            4、不带有任何参数
                直接返回一个resolved状态的Promise对象

        Promise.reject()
            返回一个新的 Promise 实例，该实例的状态为rejected

                Promise.reject('php');  等价于
                new Promise((resolve,reject)=>{
                    reject('php');
                })

            注意：
                Promise.reject()方法的参数，会原封不动地作为reject的理由，变成后续方法的参数

            例如：这个示例会直接输出thens对象。
                let thens = {
                    then:function(resolve,reject){
                        reject('1234');
                    }
                };
                let promiss = Promise.reject(thens);
                promiss.then((ret)=>{
                    console.log(ret);
                }).catch((err)=>{
                    console.log(err);
                });
        
    简单用法
        let promiss = new Promise((resolve,reject)=>{
            let err = {'code':0};
            let suc = {'code':1}
            setTimeout(()=>{
                //从pedding ->succed 或者pedding->fail 只能有一种实现，（状态只会改变一次，改变之后就不会再变了）
                resolve(suc); //从pedding ->succed   
                reject(err);//从pedding->fail
            },3000);
        });

        promiss.then((sucres)=>{
            console.log(sucres);
        },(errres)=>{
            console.log(errres);
        });

    仿写ajax
        function Ajaxget(url){
            let promiss = new Promise((resolve,reject)=>{

                let xhr = new XMLHttpRequest();
                xhr.open("GET", url);
                xhr.onreadystatechange = function(){
                    if (this.readyState !== 4) {
                    return;
                  }
                  if (this.status === 200) {
                    resolve(this.response);
                  } else {
                    reject(new Error(this.statusText));
                  }
                };
                xhr.responseType = "json";
                xhr.setRequestHeader("Accept", "application/json");
                xhr.send();
            });
            return promiss;
        }

    仿写jsonp
        function jsonp(url){
            let promiss = new Promise(function(resolve,reject){
                let script = document.createElement('script');
                 this.callback = function(ret){
                    resolve(ret);
                }
                script.src = url;
                document.body.appendChild(script);
            });
            return promiss;
        }  


    方法汇总
        Promise.prototype.then()    该方法会返回一个新的promiss对象，为promiss对象设置回调函数
        Promise.prototype.catch()   该方法会返回一个新的promiss对象，为promiss对象设置报错的回到函数
        Promise.all()               将多个promiss对象汇总成一个promiss对象，新的promiss对象的状态依赖于所有的promiss对象的值
        Promise.race()              将多个promiss对象汇总成一个promiss对象，新promiss对象的状态取决于第一个promiss对象的值
        Promise.resolve()           将一个对象转为promiss对象，默认状态为resolve;
        Promise.reject()            将一个对象转为promiss对象，默认状态为reject;