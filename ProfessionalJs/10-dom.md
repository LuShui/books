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


	元素大小
		ele.offsetWidth        元素的宽度（包含边框和padding）
		ele.offsetHeight       元素的高度（包含边框和padding）
		ele.offsetTop          元素的距离父容器顶部的高度
		ele.offsetLeft         元素的父容器左边的高度
		ele.clientWidth  	   元素宽度（包含边框）
		ele.clientHeight  	   元素高度（包含边框）	


