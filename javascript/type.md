类型判断
	1、typeof
		typeof  可以准确识别出string，boolean，undefined，number，function类型，
				但是对于Date，Error，RegExp，null 识别的结果都是object类型。


	2、Object.prototype.toString.call(type)
		现代浏览器中可以识别几乎所有的类型。

		String			[object String]
		Boolean			[object Boolean]
		Undefined		[object Undefined]
		Number			[object Number]
		Function		[object Function]
		class			[object Function]
		Null			[object Null]
		Date			[object Date]
		Error			[object Error]
		RegExp			[object RegExp]
		Promise			[object Promise]
		Array			[object Array]
		Object			[object Object]
		Set				[object Set]
		Window			[object Window]
		Math			[object Math]
		Symbol			[object Symbol] 


	3、instanceof   判断对象是否是某个类的实例，返回true或false
		只能识别new创建的对象。
		例如：a = 'string' 返回false
			  a = new String('string'); 返回true
	    但是数组是一个例外
	    	arr = []; 和 arr = new Array();都返回true
