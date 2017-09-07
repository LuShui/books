Proxy
        形式：var proxy = new Proxy(target, handler);
            target 要代理（或拦截）的目标对象
            handler：要代理（或拦截）的行为

            new Proxy()表示生成一个Proxy实例，target参数表示所要拦截的目标对象，handler参数也是一个对象，用来定制拦截行为。
            var Person = {
                name:'javascript',
                age:6
               };
            let  por = new Proxy(Person,{
                get:function (target,protype) {
                    //target   表示目标对象
                    //prptype  要访问的属性
                    console.log(target);//Object {name: "javascript", age: 6}
                    console.log(protype);//name
                    return 'this is not get'
                   }
                });
             无论输出任何属性结果都一直，即使改属性不存在
            console.log(por.name);//this is not get
        注意：要使得Proxy起作用，必须针对Proxy实例进行操作，而不是针对目标对象（Person对象）进行操作


        支持的拦截操作
            （1）get(target, propKey, receiver)
                拦截对象属性的读取，比如proxy.foo和proxy['foo']。
            （2）set(target, propKey, value, receiver)
                拦截对象属性的设置，比如proxy.foo = v或proxy['foo'] = v，返回一个布尔值。
            （3）has(target, propKey)
                拦截propKey in proxy的操作，返回一个布尔值。
            （4）deleteProperty(target, propKey)
                拦截delete proxy[propKey]的操作，返回一个布尔值。
            （5）ownKeys(target)
                拦截Object.getOwnPropertyNames(proxy)、Object.getOwnPropertySymbols(proxy)、Object.keys(proxy)，返回一个数组。
                该方法返回目标对象所有自身的属性的属性名，而Object.keys()的返回结果仅包括目标对象自身的可遍历属性。
            （6）getOwnPropertyDescriptor(target, propKey)
                拦截Object.getOwnPropertyDescriptor(proxy, propKey)，返回一个属性描述对象或者undefined。
            （7）defineProperty(target, propKey, propDesc)
                拦截Object.defineProperty(proxy, propKey, propDesc）、Object.defineProperties(proxy, propDescs)，返回一个布尔值。
            （8）preventExtensions(target)
                拦截Object.preventExtensions(proxy)，返回一个布尔值。
            （9）getPrototypeOf(target)
                拦截Object.getPrototypeOf(proxy)，返回一个对象。
            （10）isExtensible(target)
                拦截Object.isExtensible(proxy)，返回一个布尔值。
            （11）setPrototypeOf(target, proto)
                拦截Object.setPrototypeOf(proxy, proto)，返回一个布尔值。
                如果目标对象是函数，那么还有两种额外操作可以拦截。
            （12）apply(target, object, args)
                拦截 Proxy 实例作为函数调用的操作，比如proxy(...args)、proxy.call(object, ...args)、proxy.apply(...)。
            （13）construct(target, args)
                拦截 Proxy 实例作为构造函数调用的操作，比如new proxy(...args)。
