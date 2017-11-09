javascript的词法作用域和动态作用域
	词法作用域（静态作用域）：函数的作用域在函数定义的时候就决定了	
	动态作用域：			  函数的作用域是在函数调用的时候才决定的
	JavaScript采用词法作用域（静态作用域）

		var value = 10;
		function fot(){
			console.log(value); //这里输出是多少？
		}
		function bar(){
			var value = 1;
			fot();
		}
		bar();//结果为10
		分析：JavaScript是词法作用域，也就是静态作用域，
				当函数使用一个变量是，首先查找局部作用域内是否存在，不存在则查找全局作用域。
				所以value在函数作用域内不存在，全局作用域中存在。所以是10.



JavaScript执行上下文
	当遇到函数执行时，就会创建一个JavaScript执行上下文

	函数执行包含3个对象
		变量对象(Variable object，VO)
		作用域链(Scope chain)
		this(确定this指向)
	
	执行过程(执行过程分为2个步骤)
		1、进入执行上下文
			在进入执行上下文时，首先会处理函数声明，其次会处理变量声明，如果如果变量名称跟已经声明的形式参数或函数相同，则变量声明不会干扰已经存在的这类属性
			当进入执行上下文时，这时候还没有执行代码，
				变量对象会包括：

					函数的所有形参 (如果是函数上下文)
						由名称和对应值组成的一个变量对象的属性被创建
						没有实参，属性值设为 undefined

					函数声明
						由名称和对应值（函数对象(function-object)）组成一个变量对象的属性被创建
						如果变量对象已经存在相同名称的属性，则完全替换这个属性

					变量声明
						由名称和对应值（undefined）组成一个变量对象的属性被创建；
						如果变量名称跟已经声明的形式参数或函数相同，则变量声明不会干扰已经存在的这类属性
		2、代码执行
			在代码执行阶段，会顺序执行代码，根据代码，修改变量对象的值



JavaScript解读this
	函数调用的时候，如何确定 this 的取值
		1.计算 MemberExpression 的结果赋值给 ref

		2.判断 ref 是不是一个 Reference 类型
			2.1 如果 ref 是 Reference，并且 IsPropertyReference(ref) 是 true, 那么 this 的值为 GetBase(ref) 
				IsPropertyReference(ref) 检测ref的base值是否是一个对象，是返回true否则返回false
				GetBase(ref)    获取ref的base值
			2.2 如果 ref 是 Reference，并且 base value 值是 Environment Record, 那么this的值为 ImplicitThisValue(ref)  
				ImplicitThisValue(ref)  该函数始终返回undefined
			2.3 如果 ref 不是 Reference，那么 this 的值为 undefined
				

		





