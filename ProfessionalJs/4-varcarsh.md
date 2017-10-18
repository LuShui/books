变量，作用域，内存相关

1、变量
	JavaScript是一门动态语言（弱类型），可以实时为对象增加属性
	变量之间的赋值
		基本类型（string，undefined，number，Boolean）参数传递是值传递
		对象类型参数传递是引用传递

	函数参数之间的传递
		所有的函数参数都是使用值传递
			//函数之间传参使用值传递(普通类型)
			var obj = '123';
			function setname(obj){
				obj = 234; //这里修改obj的值
			}
			setname(obj);
			console.log(obj);//输出123


			//对象类型函数传参
			var obj2 = {};
			function setage(obj2){
				obj2.age = 22;//为对象添加属性
				obj2 = new Date(); //修改obj2的指向
				console.log(obj2);//Fri Sep 29 2017 15:24:38 GMT+0800
			}
			setage(obj2);
			console.log(obj2);//{age: 22}

	类型检测
		typeof		可以检测基本类型
		instanceof  判段属于某个类的实例，（可以检测对象类型）
		

2、作用域
	作用域中的变量只能递增级访问（函数作用域访问全局）
	每一个作用域都有一个与之对应环境，同样也有着一个对应的环境变量，


3、内存管理
	JavaScript的内存管理是自动管理，不需要手动管理（垃圾收集）
	垃圾收集方式
	1、标记清除
		这是当前主流的垃圾收集方式。给不需要的变量打上可以回收的标记，然后回收它占用的内存

	2、引用计数	
		对变量没使用一次，引用计数就+1，直到引用计数为0是，回收其占用的内存

