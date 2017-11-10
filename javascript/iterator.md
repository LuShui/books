Iterator(遍历器)
	含义：它是一种接口，为各种不同的数据结构提供统一的访问机制。任何数据结构只要部署Iterator接口，就可以完成遍历操作

	对象部署：
		默认的 Iterator 接口部署在数据结构的Symbol.iterator属性，或者说，一个数据结构只要具有Symbol.iterator属性，就可以认为是“可遍历的”（iterable）

	原生具备 Iterator 接口的数据结构如下。
		Array
		Map
		Set
		String
		TypedArray
		函数的 arguments 对象
		NodeList 对象

	作用：
		1、是为各种数据结构，提供一个统一的、简便的访问接口；
		2、是使得数据结构的成员能够按某种次序排列；
		3、是ES6创造了一种新的遍历命令for...of循环，Iterator接口主要供for...of消费


	模拟实现
		function myIterator(array){
			let index = 0;
			let len = array.length;
			return {
				next:function(){
					return index < len ? {'value':array[index++],'done':false} : {'value':undefined,'done':true};
				}
			}
		}
		let itear = myIterator([1,2,3,4,5,6,7]);
		console.log(itear.next());  {value: 1, done: false}
		console.log(itear.next());	{value: 2, done: false}

		注：next()返回一个对象，对象的元素包好value和done两个属性
			value 	指元素的值
			done 	表示是否是最后一个元素，是最后一个元素为true，否则为false


	运行逻辑：
		1、创建一个指针对象，指向第一个元素
		2、调用next()使指针指向第二个元素
		3、重复第二步一直到最后一个元素


	调用 Iterator 接口的场合
		有一些场合会默认调用 Iterator 接口（即Symbol.iterator方法）
		1、for...of
		2、解构赋值，对数组和 Set 结构进行解构赋值时
		3、扩展运算符，扩展运算符（...）也会调用默认的 Iterator 接口
		4、yield*后面跟的是一个可遍历的结构，它会调用该结构的遍历器接口
		5、任何接受数组作为参数的场合，其实都调用了遍历器接口


	遍历器对象的return()，throw()
		遍历器对象除了具有next方法，还可以具有return方法和throw方法。
		如果你自己部署遍历器对象生成函数，那么next方法是必须部署的，return方法和throw方法是否部署是可选的
			return()
				如果for...of循环提前退出（通常是因为出错，或者有break语句或continue语句），就会调用return方法。
				如果一个对象在完成遍历前，需要清理或释放资源，就可以部署return方法



