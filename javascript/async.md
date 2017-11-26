ES2017 标准引入了 async 函数，使得异步操作变得更加方便。它的本质是 Generator 函数的语法糖。

	和Generator相比
		* 替换成了 async
		yield 替换成了 await
		Generator 函数调用后返回一个 Iterator 遍历器
		async 函数调用后返回Promiss对象



	async函数对 Generator 函数的改进
		内置执行器
			不需要像 Generator 函数那样需要用next()调用，直接和普通函数一样直接调用
		更好的语义
			async和await，比起星号和yield，语义更清楚
		更广的适用性
			co模块约定，yield命令后面只能是 Thunk 函数或 Promise 对象，而async函数的await命令后面，可以是Promise 对象和原始类型的值
		返回值是 Promise

	

	基本用法
		function timeout(ms) {
		  return new Promise((resolve) => {
		    setTimeout(resolve(123), ms);
		  });
		}

		async function asyncPrint(value, ms) {
		  let ret = await timeout(ms);
		  console.log(value);
		  return ret;
		}

		asyncPrint('hello world', 3000).then((ret)=>{
			console.log(ret); 123
		});


	语法

		1、async函数内部return语句返回的值，会成为then方法回调函数的参数

		2、async函数内部抛出错误，会导致返回的 Promise 对象变为reject状态。抛出的错误对象会被catch方法回调函数接收到

		3、async函数返回的 Promise 对象，必须等到内部所有await命令后面的 Promise 对象执行完，才会发生状态改变，
		除非遇到return语句或者抛出错误。也就是说，只有async函数内部的异步操作执行完，才会执行then方法指定的回调函数

		await 命令：
			await命令后面是一个 Promise 对象。如果不是，会被转成一个立即resolve的 Promise 对象




	
