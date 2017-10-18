事件
	事件流
		1、冒泡事件
			从目标元素一直传递到document
		2、捕获事件
			从document传递到目标元素
		3、Dom事件流
			DOM2事件规定事件流包括3个阶段，事件捕获阶段，处于目标阶段，事件冒泡阶段
			首先发生的是事件捕获阶段(为截获事件提供机会)，然后是处于目标阶段，最后是冒泡阶段(冒泡事件做出响应)

	事件处理程序
		1、Dom0
			ele.onclick = function(){}

		2、Dom2
			ele.addEventListener()
			ele.removeEventListener()



from表单
	一些属性和方法
	acceptCharset 	字符集
	action	        接受请求的url
	elements		表单中所有控件的集合
	entype			请求的编码类型
	length			表单中所有控件数量
	method			http请求类型，get。post
	name			表单名称
	reset() 		重置表单
	submit() 		提交表单
	target			发送请求和接受响应的窗口


