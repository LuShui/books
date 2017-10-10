通过link预加载资源
	通过rel="preload"进行内容预加载
	 link元素的 rel 属性的属性值preload能够让你在你的HTML页面中 head元素内部书写一些声明式的资源获取请求，可以指明哪些资源是在页面加载完成后即刻需要的。
	 对于这种即刻需要的资源，能在页面加载的生命周期的早期阶段就开始获取，在浏览器的主渲染机制介入前就进行预加载。
	 这一机制使得资源可以更早的得到加载并可用，且更不易阻塞页面的初步渲染，进而提升性能

	 将使用preload作为rel属性的属性值。这种做法将把 link 元素塞入一个预加载器中，这个预加载器也将用于其他我们所需要的，各种各样的，任意类型的资源
	 通过 href和as 属性指定需要被预加载资源的资源路径及其类型
	 	例如：
	 	预加载css
	 	<link rel="preload" href="style.css" as="style">
	 	预加载JavaScript
  		<link rel="preload" href="main.js" as="script">

  	优点：
	  	更精确地优化资源加载优先级。
		匹配未来的加载需求，在适当的情况下，重复利用同一资源。
		为资源应用正确的内容安全策略。
		为资源设置正确的 Accept 请求头

	可以预加载的属性：
		audio: 音频文件。
		document: 一个将要被嵌入到 frame 或 iframe 内部的HTML文档。
		embed: 一个将要被嵌入到<embed>元素内部的资源。
		fetch: 那些将要通过fetch和XHR请求来获取的资源，比如一个ArrayBuffer或JSON文件。
		font: 字体文件。
		image: 图片文件。
		object: 一个将会被嵌入到<embed>元素内的文件。
		script: JavaScript文件。
		style: 样式表。
		track: WebVTT文件。
		worker: 一个JavaScript的web worker或shared worker。
		video: 视频文件。


	判断浏览器是否支持某种数据类型：
		link 元素可以接受一个type属性。这一属性可以包含该元素所指向资源的MIME类型。在浏览器进行预加载的时候，这个属性值将会非常有用——浏览器将使用type属性来判断它是否支持这一资源，如果浏览器支持这一类型资源的预加载，下载将会开始，否则便对其加以忽略
		  <link rel="preload" href="sintel-short.mp4" as="video" type="video/mp4">



