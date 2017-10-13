otherWindow.postMessage(message, targetOrigin)   跨文档消息传送
	otherWindow：其他窗口的一个引用，比如iframe的contentWindow属性、执行window.open返回的窗口对象、或者是命名过或数值索引的window.frames
	message：将要发送到其他 window的数据
	targetOrigin：通过窗口的origin属性来指定哪些窗口能接收到消息事件