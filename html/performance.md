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
	