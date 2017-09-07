属性描述对象
    含义：JavaScript提供了一个内部数据结构，用来描述一个对象的属性的行为，控制它的行为。
    每个属性都有自己对应的属性描述对象，保存该属性的一些元信息。
    属性描述对象提供6个元属性。
    （1）value
        value存放该属性的属性值，默认为undefined。
    （2）writable
        writable存放一个布尔值，表示属性值（value）是否可改变，默认为true。
    （3）enumerable
        enumerable存放一个布尔值，表示该属性是否可枚举，默认为true。
        如果设为false，会使得某些操作（比如for...in循环、Object.keys()）跳过该属性。
    （4）configurable
        configurable存放一个布尔值，表示“可配置性”，默认为true。
        如果设为false，将阻止某些操作改写该属性，比如，无法删除该属性，也不得改变该属性的属性描述对象（value属性除外）。
        也就是说，configurable属性控制了属性描述对象的可写性。
    （5）get
        get存放一个函数，表示该属性的取值函数（getter），默认为undefined。
    （6）set
        set存放一个函数，表示该属性的存值函数（setter），默认为undefined。


    function Person() {
        this.name = 'javascript';
        this.version = 6;
        this.getAttribute = function () {
        }
    };
    let person = new Person();



获取属性描述对象
    Object.getOwnPropertyDescriptor()可以获取属性描述对象
        他接受两个参数，第一个为需要获取的对象，第二个为需要获取的属性
        案例：获取person对象的name属性
        let attObj = Object.getOwnPropertyDescriptor(person,'name');
        console.log(attObj);{configurable:true,enumerable:true,value:"javascript",writable:true}

修改或者新增属性
    Object.defineProperty()方法可以新增或者修改对象描述属性(单个属性操作)
        他接受3个参数
        第一个为需要修改的对象
        第二个为需要修改的属性（如果不存在则新增属性）
        第三个为对象的描述对象
    Object.defineProperty(person,'name',{
        value:'css'
    });
    let attObj = Object.getOwnPropertyDescriptor(person,'name');
    console.log(attObj);{value: "css", writable: true, enumerable: true, configurable: true}

    Object.defineProperties()方法同时新增或修改多个属性
        他接受2个参数
        第一个为需要求改的对象
        第二个为属性描述的集合
        案例：修改person对象的name属性以及新增age属性
         Object.defineProperties(person,{
            'name':{value:'css'},
            'age':{value:1}
        });
    注意：以上两个方法一旦定义了取值函数get（或存值函数set），就不能将writable设为true，或者同时定义value属性，会报错.
            如果未设置writable、configurable、enumerable，则这三个属性的默认值都为false