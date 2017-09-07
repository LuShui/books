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

    super 关键字
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


    静态属性和静态方法
        静态属性：
            通过直接定义在类上的属性是静态属性
        静态方法
            通过static关键字定义

        静态属性与静态方法都无法继承
        class Person{
            constructor(name = 'es6',age = 6,sex = 'man'){
                this.name = name;
                this.age = age;
                this.sex = sex;
            }
            static maek(){
                console.log('make');
            }
        }
        Person.base = 'base';

        class Man extends Person{
            constructor(){
                super();
            }
        }
        let man = new Man();
        console.log(man.base);//undefined
        man.make();//man.make is not a function