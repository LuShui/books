Reflect
        作用：   1、ES6提供的操作对象的新API
                2、讲Object上的一些方法部署到该对象上。
                3、该对象的API与Proxy能够代理的方法意义对应。

        部署的静态方法
            Reflect对象一共有13个静态方法。
                 Reflect.apply(target,thisArg,args)
                    Reflect.apply方法等同于Function.prototype.apply.call(func, thisArg, args)，用于绑定this对象后执行给定函数
                Reflect.construct(target,args)
                Reflect.get(target,name,receiver)
                    查找并返回target对象的name属性，如果没有该属性，则返回undefined

                Reflect.set(target,name,value,receiver)
                    设置target对象的name属性等于value
                    Reflect.set会触发Proxy.defineProperty拦截

                Reflect.defineProperty(target,name,desc)
                    基本等同于Object.defineProperty，用来为target对象定义属性
                Reflect.deleteProperty(target,name)
                    用于删除target对象的name属性

                Reflect.has(target,name)
                    name是否为target的属性，对应name in obj里面的in运算符

                Reflect.ownKeys(target)
                    Reflect.ownKeys方法用于返回对象的所有属性，
                    基本等同于Object.getOwnPropertyNames与Object.getOwnPropertySymbols之和。

                Reflect.isExtensible(target)
                    Reflect.isExtensible方法对应Object.isExtensible，返回一个布尔值，表示target对象是否可扩展
                    如果参数不是对象，Object.isExtensible会返回false，因为非对象本来就是不可扩展的，而Reflect.isExtensible会报错

                Reflect.preventExtensions(target)
                    Reflect.preventExtensions对应Object.preventExtensions方法，用于让target对象变为不可扩展。
                    它返回一个布尔值，表示是否操作成功

                Reflect.getOwnPropertyDescriptor(target, name)
                    Reflect.getOwnPropertyDescriptor基本等同于Object.getOwnPropertyDescriptor，
                    用于得到target对象name属性的描述对象
                    区别：如果第一个参数不是对象
                        Object.getOwnPropertyDescriptor(1, 'foo')不报错，返回undefined，
                        而Reflect.getOwnPropertyDescriptor(1, 'foo')会抛出错误，表示参数非法

                Reflect.getPrototypeOf(target)
                    Reflect.getPrototypeOf方法用于读取target对象的__proto__属性，对应Object.getPrototypeOf(obj)。
                    区别：
                        如果参数不是对象，Object.getPrototypeOf会将这个参数转为对象，然后再运行，
                        而Reflect.getPrototypeOf会报错。

                Reflect.setPrototypeOf(target, prototype)
                    用于设置target对象的__proto__属性，返回第一个参数对象，对应Object.setPrototypeOf(obj, newProto)。
                    区别：
                        如果第一个参数不是对象，Object.setPrototypeOf会返回第一个参数本身，而Reflect.setPrototypeOf会报错
                        如果第一个参数是undefined或null，Object.setPrototypeOf和Reflect.setPrototypeOf都会报错。

            上面这些方法的作用，大部分与Object对象的同名方法的作用都是相同的，
            而且它与Proxy对象的方法是一一对应的。


        各自的描述
            Reflect.get(target,name,receiver) //查找并返回target对象的name属性，如果没有该属性，则返回undefined
                如果第一个参数不是对象，Reflect.get方法会报错
                var person = {
                    name:'javascript',
                    version:2015
                };
                console.log(Reflect.get(person,'name'));//javascript


            Reflect.set(target, name, value, receiver)//设置target对象的name属性等于value。
                var person = {
                    name:'javascript',
                    version:2015
                   };
                Reflect.set(person,'name','java');
                console.log(Reflect.get(person,'name'));//java


            Reflect.has(target,name)//判断name是否为target的属性
                var person = {
                    name:'javascript',
                    version:2015
                };
                console.log(Reflect.has(person,'name'));true


        Reflect.deleteProperty(obj, name)
            Reflect.deleteProperty方法等同于delete obj[name]，用于删除对象的属性
                var person = {
                     name:'javascript',
                    version:2015
                 };
                Reflect.deleteProperty(person,'name');
                console.log(person);//{version: 2015}