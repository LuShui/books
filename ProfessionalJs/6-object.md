1、面向对象基础
	var json = {};
	Object.defineProperty() 新增或者修改对象描述属性
		3个参数，
			第一个是需要新增或修改属性的对象
			第二个是新增或者修改的属性名称
			第三个是一个属性描述对象（对该属性特征的一些描述）
		Object.defineProperty(json,'name',{
			enumerable:true,
		});


	Object.defineProperties() 新增或修改多个属性
		Object.defineProperties(json,{
			age:{
				enumerable:true,
			},
			sex:{
				enumerable:true,
			}
		});


	Object.getOwnPropertyDescriptor() 获取属性描述对象
		let desc = Object.getOwnPropertyDescriptor(json,'name');
		属性描述对象：提供6个元属性
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


2、创建对象
	原型的理解   prototype，__proto__，constructor 三个属性之间的恩怨情仇
		prototype 		：	是函数上的属性
		__proto__ 		：  是通过构造函数创建的对象上的属性
		constructor     ：  是prototype上的属性

		Person.prototype.constructor = Person
		Person.prototype.constructor = p.__proto__.constructor
		Person.prototype = p.__proto__


	1、工厂模式
		通过一个函数快速的创建对象

	2、构造函数模式
		通过自定义构造函数创建对象。
			function Person(){
				this.name = 'ls';
				this.age = 24;
				this.say = function(){
					console.log('hello');
				}
			}
		内部逻辑：
		1、一个新对象被创建。它继承自Person.prototype;     
			let obj = {};
			obj.__proto__ == Person.prototype
		2、调用Person函数，并将Person中的this的指向为obj
		3、返回obj对象
			代码说明
			function Per2(){
				let obj = {};
				obj.__proto__ = Person.prototype;
				Person.call(obj);
				return obj;
			}
			let p = new Person();
			let p2 = Per2();
			p2.say();//hello
			console.log(p2 instanceof Person);//true

	3、原型模式
		理解原型：
			创建一个函数时，会自动生成一个prototype属相，这个属性指向函数的原型对象
			所有的原型对象都有一个constructor属性（构造函数），这个属性包含一个指向prototype属性所在函数的指针。例如 Person.prototype.constructor == Person
			Person.prototype.isPrototypeOf(p2) //判断Person.prototype是否是p2的原型
			Object.getPrototypeOf(p2)          //获取P2的原型

		问题：所有的实例在默认情况下的结构都是一致的，没有单独的私有属性。


	4、组合使用构造函数模式和原型模式（最常用的方式）
		集构造函数模式与原型模式两家之长的方式创建对象，既可以拥有自己的私有属性，同时也可以拥有共享的公共方法。

	5、动态原型模式
		通过检查某个函数是否存在，不存在则将函数添加到原型上。

	6、寄生构造模式
		创建一个函数，在函数中创建一个新对象，并以相应的属性和方法初始化新对象，最后通过return返回新对象。
		该方式和工厂模式类似

	7、稳妥对象模式
		前提：不能使用this和new光建子。
		定义一个函数，创建一个空对象。并以相应的属性和方法初始化新对象，最后通过return返回新对象。函数的结果就需要创建的对象。





3、继承
	JavaScript只支持实现继承，不支持接口继承。而且继承是通过原型链实现的。。

	1、原型链继承
		将子类的原型指向需要继承的类的一个实例。
		function Person(){
			this.name = 'name';
		}
		Person.prototype.myname = function(){
			console.log(this.name);
		}
		function SubPerson(){
			//重写了Person的属性
			this.name = 'subname';
		}
		SubPerson.prototype = new Person();
		let sub= new SubPerson();
		//继承了Person类的属性和方法
		sub.myname();//subname

	2、借用构造函数继承
		在子类中调用父类的构造函数，并修改this指向。将父类的this指向为子类
		function Person(){
			this.name = 'php';
		}
		function subPerson(){
			Person.call(this);
		}
		let sub = new subPerson();
		console.log(sub.name);

		缺点：
			1、只是调用了构造函数，原型上的属性或者方法没有被继承
			2、由于原型指向不一样，所以  instanceof  关键字判断结果为false


	3、组合继承（原型链继承和借用构造函数继承组合模式）
		function Person(){
			this.name = 'php';
		}
		Person.prototype.sayname = function(){
			console.log(this.name);
		}
		function subPerson(){
			Person.call(this);
		}
		subPerson.prototype = new Person();
		let sub = new subPerson();
		sub.sayname();

		缺点：会调用两次父类的方法


	4、原型式继承 （与Object.create()类似）
		function object(obj){
			function O(){};
			O.prototype = obj;
			let o = new O();
			return o;
		}
		let json = {
			'name':'php',
			'array':[1,2,3,4,5]
		}
		let sub = object(json);
		console.log(json);//{name: "php", array: Array[5]}

	5、寄生式继承 （在原型式继承的方案上再加以改进的一种方式）
		function object(obj){
			function O(){};
			O.prototype = obj;
			let o = new O();
			return o;
		}
		let json = {
			'name':'php',
			'array':[1,2,3,4,5]
		}
		function subPerson(obj){
			let newobj = object(obj);
			newobj.say = function(){

			}
		}
		let sub = subPerson(json);

	6、寄生组合继承 （集众家之长的方案，比较普遍的一种方式）
		function object(obj){
			function O(){};
			O.prototype = obj;
			let o = new O();
			return o;
		}
		function innerobj(supcls,subcls){
			var prototype = object(supcls.prototype);
			prototype.constructor = subcls;
			subcls.prototype = prototype;
		}
		function Person(){
			this.name = 'name';
		}
		Person.prototype.myname = function(){
			console.log(this.name);
		}
		function SubPerson(){
			Person.call(this);
		}
		innerobj(Person,SubPerson);
		let p = new SubPerson();
		p.myname();