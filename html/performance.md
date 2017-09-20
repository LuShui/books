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
	
	基本使用
		let xhr = new XMLHttpRequest();
		xhr.open('GET', './xhr.php');
		
		xhr.overrideMimeType('text/xml; charset = utf-8');//Level 1设置返回的数据类型
		xhr.responseType = 'json';//Level 2设置返回的数据类型
		小结：
			xhr.overrideMimeType()能做到的xhr.responseType都能做到。
			所以现在完全可以摒弃使用xhr.overrideMimeType()

		获取response数据
			xhr提供了3个属性来获取请求返回的数据
			分别是：xhr.response、xhr.responseText、xhr.responseXML

		追踪ajax请求的当前状态
			用xhr.readyState这个属性是只读属性，总共有5种可能值，分别对应xhr不同的不同阶段
			每次xhr.readyState的值发生变化时，都会触发xhr.onreadystatechange事件
				0：UNSENT (初始状态，未打开)	此时xhr对象被成功构造，open()方法还未被调用
				1：OPENED (已打开，未发送)	open()方法已被成功调用，send()方法还未被调用。
				2：HEADERS_RECEIVED (已获取响应头)	send()方法已经被调用, 响应头和响应状态已经返回
				3:LOADING (正在下载响应体)	响应体(response entity body)正在下载中，此状态下通过xhr.response 可能已经有了响应数据
				4：DONE (整个数据传输过程结束)	整个数据传输过程结束，不管本次请求是成功还是失败

		设置请求的超时时间
			xhr.timeout
				单位：毫秒
				默认值：0，即不设置超时

		获取上传、下载的进度
			可以通过onprogress事件来实时显示进度，默认情况下这个事件每50ms触发一次。
			需要注意的是，上传过程和下载过程触发的是不同对象的onprogress事件
				上传触发的是xhr.upload对象的 onprogress事件
				下载触发的是xhr对象的onprogress事件

		事件
			onreadystatechange		
				每当xhr.readyState改变时触发；但xhr.readyState由非0值变为0时不触发。
			onloadstart				
				调用xhr.send()方法后立即触发，若xhr.send()未被调用则不会触发此事件。
			onprogress				
				xhr.upload.onprogress在上传阶段(即xhr.send()之后，xhr.readystate=2之前)触发，每50ms触发一次；xhr.onprogress在下载阶段（即xhr.readystate=3时）触发，每50ms触发一次。
			onload					
				当请求成功完成时触发，此时xhr.readystate=4
			onloadend				
				当请求结束（包括请求成功和请求失败）时触发
			onabort					
				当调用xhr.abort()后触发
			ontimeout				
				xhr.timeout不等于0，由请求开始即onloadstart开始算起，当到达xhr.timeout所设置时间请求还未结束即onloadend，则触发此事件。
			onerror					
				在请求过程中，若发生Network error则会触发此事件（若发生Network error时，上传还没有结束，则会先触发xhr.upload.onerror，再触发xhr.onerror；
				若发生Network error时，上传已经结束，则只会触发xhr.onerror）。
				注意，只有发生了网络层级别的异常才会触发此事件，对于应用层级别的异常，如响应返回的xhr.statusCode是4xx时，并不属于Network error，所以不会触发onerror事件，而是会触发onload事件。

		事件触发顺序
			

		xhr.send();
		xhr.onreadystatechange = function(){
			console.log(xhr);
		};


4、跨域方案
	1、jsonp跨域    
		通过动态的创建script标签，再指定回调函数
		只能是get请求，而且请求的url连接有长度限制

	2、document.domain + iframe跨域（数据通信）    
		此方案仅限主域相同，子域不同的跨域应用场景。
		两个页面都通过js强制设置document.domain为基础主域，就实现了同域。

	3、 location.hash + iframe跨域
	

	4、window.name + iframe跨域


	5、postMessage跨域


	6、 跨域资源共享（CORS）
		普通跨域请求：只服务端设置Access-Control-Allow-Origin即可，前端无须设置，
		若要带cookie请求：前后端都需要设置。   
			前端设置：cookiexhr.withCredentials = true 设置携带cookie
			后端设置：Access-Control-Allow-Credentials: true	设置允许cookie
					  Access-Control-Allow-Origin: http://www.lushui.com   设置允许跨域访问的域名



