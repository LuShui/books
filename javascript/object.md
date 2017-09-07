1、属性的简洁表示法
        ES6 允许直接写入变量和函数，作为对象的属性和方法
            let name = 'javascript';
            let person = {name};  =》    let person = {name:'javascript'};
            console.log(person);//{name: "javascript"}

            let person = {
                name(){
                    console.log('javascript');
                }
             }      ====》
            let person = {
                name:function(){
                    console.log('javascript');
                }
            }


     2、属性名表达式
        es5定义属性
            let person.name = 'javascript';
        es6新增
            let name = 'javascript';
            let person[name] = 'javascript';   等价于  let person.javascript = 'javascript';


     3、Object.is()  比较两个值是否严格相等（+0不等于-0，NaN等于自身）
        与其他比较运算符的比较
            ==     简单的比较是否相等，不同类型比较会自动转换
            ===    严格比较，不会自动转换类型但是NaN不等于NaN本身


     4、Object.assign()
        用于对象的合并，将源对象（source）的所有可枚举属性，复制到目标对象（target）
        Object.assign方法的第一个参数是目标对象，后面的参数都是源对象
        如果只有一个参数，Object.assign会直接返回该参数。
        如果该参数不是对象，则会先转成对象，然后返回。
        Object.assign方法实行的是浅拷贝，而不是深拷贝。
        也就是说，如果源对象某个属性的值是对象，那么目标对象拷贝得到的是这个对象的引用。


     6、属性的可枚举性
        对象的每个属性都有一个描述对象（Descriptor），用来控制该属性的行为。
        Object.getOwnPropertyDescriptor方法可以获取该属性的描述对象。
            let Person = {
                name:'javascript',
                version:6
            };
            let des = Object.getOwnPropertyDescriptor(Person,'name');
            console.log(des);   // {value: "javascript", writable: true, enumerable: true, configurable: true}

    7、属性的遍历
     ES6一共有5种方法可以遍历对象的属性。
        （1）for...in
            for...in循环遍历对象自身的和继承的可枚举属性（不含Symbol属性）。
        （2）Object.keys(obj)
            Object.keys返回一个数组，包括对象自身的（不含继承的）所有可枚举属性（不含Symbol属性）。
        （3）Object.getOwnPropertyNames(obj)
            Object.getOwnPropertyNames返回一个数组，包含对象自身的所有属性（不含Symbol属性，但是包括不可枚举属性）。
        （4）Object.getOwnPropertySymbols(obj)
            Object.getOwnPropertySymbols返回一个数组，包含对象自身的所有Symbol属性。
        （5）Reflect.ownKeys(obj)
             Reflect.ownKeys返回一个数组，包含对象自身的所有属性，不管属性名是Symbol或字符串，也不管是否可枚举。


     8、Object.keys()，Object.values()，Object.entries()
        Object.keys
            返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键名
        Object.values
            返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键值
        Object.entries
            返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键值对数组

    9、Object.getOwnPropertyDescriptors方法，返回指定对象所有自身属性（非继承属性）的描述对象
