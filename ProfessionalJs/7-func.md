1、递归
	函数调用自身就形成了递归函数

2、闭包
	闭包是指有权访问另一个函数作用域中的变量的函数
	闭包实现
		let a = 20;
	 	function base(){
	 		let a = 10;
	 		return function(){
	 			return a;
	 		}
	 	}
	 	let b = base()();
	 	console.log(b);


3、模仿块级作用域
	通过只执行行数实现

4、私有变量
	函数内的变量可以成为私有变量。
