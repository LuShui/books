DOM操作
	通过一个css选择符查找元素
	1、querySelector()      只会查找到第一个，如何没有找到则为null
	2、querySelectorAll() 	会查找所有的元素，返回一个nodeList对象，如果没有找到，则返回一个空的nodeList对象

	
	一些属性和方法
	document.activeElement  	获取焦点的元素
	document.hasFocus() 		检测文档是否获得了焦点
	document.readyState 		文档的状态   值为 loading   complete
	document.compatMode 		浏览器渲染模式     CSS1Compat标准模式    BackCompat兼容模式
	ele.scrollIntoView() 		让某个元素可见

