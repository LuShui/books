1、前端性能优化
	1、减少http请求，合并压缩js和css
	2、使用浏览器缓存，减少数据传输大小。
	3、CSS放在页面最上部，javascript放在页面最下面
	4、图片懒加载，只加载当前屏的图片。（减少了http请求）
	5、减少dom操作

	页面渲染优化
		1、动态加载脚本，通过JavaScript来实现脚本加载
			function loadJS(src) {
	  			const script = document.createElement('script');
	  			script.src = src;
	  				document.getElementsByTagName('head')[0].appendChild(script);
			}
			loadJS('http://example.com/scq000.js');

		2、异步加载脚本，async和defer可是实现脚本异步加载
			async和defer区别：async属性的脚本执行顺序是不能得到保证的。而使用defer属性的脚本执行顺序可以得到保证
				defer属性是在html文档解析完成后，DOMContentLoaded事件之前就会执行js。async一旦加载完js后就会马上执行，最迟不超过window.onload事件
				如果脚本没有操作DOM等元素，或者与DOM时候加载完成无关，直接使用async。如果需要DOM，就使用defer

		3、DNS Prefetch 预解析
			<meta http-equiv="x-dns-prefetch-control" content="on" /> /* 这是用来告知浏览器当前页面要做DNS预解析 */
			<link rel="dns-prefetch" href="//example.com">



2、缓存
	1、强缓存
	2、协商缓存
	


3、XMLHttpRequest
	XMLHttpRequest标准又分为Level 1和Level 2
	Level 1缺点：
		受同源策略的限制，不能发送跨域请求
		不能发送二进制文件（如图片、视频、音频等），只能发送纯文本数据
		在发送和获取数据的过程中，无法实时获取进度信息，只能判断是否完成
	Level 2新增功能
		可以发送跨域请求，在服务端允许的情况下
		支持发送和接收二进制数据
		新增formData对象，支持发送表单数据
		发送和获取数据时，可以获取进度信息
		可以设置请求的超时时间