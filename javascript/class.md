class:定义类的关键字
    使用class定义类与使用函数定义类其实没有多大的差别。
    只是使用class定义更清晰易懂。


 constructor()方法：类的构造方法，通过new创建对象时会调用该方法。
    该方法是类的默认方法，同时也是类必须的方法，
    如果一个类没有显示的定义，一个空的constructor方法会被默认添加

    class 定义类实例
        class Person{
            constructor(name = 'es6',age = 6,sex = 'man'){
                this.name = name;
                this.age = age;
                this.sex = sex;
            }
            logname(){
                console.log(this.name);
            }
            logage(){
                console.log(this.age);
            }
            logsex(){
                console.log(this.sex);
            }
        }
        let person = new Person();
        person.logname();//es6
        person.logage();//6
        person.logsex();//man



Class 的静态方法
    类相当于实例的原型，所有在类中定义的方法，都会被实例继承。如果在一个方法前，加上static关键字，就表示该方法不会被实例继承，而是直接通过类来调用，这就称为“静态方法”。
         class Person{
            constructor(name = 'es6',age = 6,sex = 'man'){
                this.name = name;
                this.age = age;
                this.sex = sex;
            }
            static logname(){
                console.log(this.name);//this指向Person
            }
        }
        Person.logname();


    
注：
    class定义的方法或者属性默认都是声明在原型上的，只有显示声明定义在this上，才不是定义在原型上面

    类不存在变量提升
         let p = new Person; //Person is not defined
         class Person{}

    



 extends：类的继承

    class Man extends Person{
     }
    let man = new man();//在这里会报错
        在子类中必须先调用父类的构造方法。
        因为子类没有自己的this指向，必须先获取父类的this指向。

    class Man extends Person{
        constructor(){
            super();
        }
    }
    let man = new Man();

 Extends 的继承目标
    子类继承Object类。
        这个时候子类其实是父类的复制。子类的对象其实就是Object的对象
        class Meobject extends Object{
            constructor(){
                super();
            }
        }
        let meobj = new Meobject();
        let obj = new Object();
        console.log(meobj instanceof Object);//true
        console.log(obj instanceof Meobject);//false

    getPrototypeOf()获取父类
         console.log(Object.getPrototypeOf(meobj));//Object{}

    super 关键字 ES6 要求，子类的构造函数必须执行一次super函数
        1、当super当函数使用时，表示父类的构造方法
        2、当super当对象调用方法时，表示父类的对象。同时会绑定子类的this对象
        class Man extends Person{
            constructor(){
                super();
                this.name = 'php';
                super.logname();//php
            }
        }
        let man = new Man();