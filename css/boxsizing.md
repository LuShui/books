css盒模型
	盒模型分为IE盒模型和W3C标准盒模型

	IE盒模型：
		width等于 元素的宽度（width） + 边框的宽度（border width） + padding
		
	W3C标准盒模型：
		width 等于元素的宽度（width）

	box-sizing  设置盒模型组成模式
		content-box：	W3C标准盒模型	width = content width
		border-box：	IE盒模型		width = content width + padding width + border width

	备注：
		早期的IE（5.5版本）用的是IE盒模型，而从IE6开始，只要在文档中声明（添加doctype）则，兼容使用W3C盒模型。
		如果IE678未添加doctype，即怪异模式，那么也是用IE模型。
		从IE9以后，则不用填写声名也用的是W3C模型。

		所有的盒模型，只要没有添加doctype，都处于怪异模式，但此时，只有ie678使用ie盒模型，
		其他的虽然处于怪异模式，但仍旧使用标准模型，其实与普通模式效果相同,怪异模式是在ie6时代为了兼容ie5以及以前版本的浏览器保留的 现在实际使用中都使用标准模式添加doctype


隐藏元素的方式
	1、opacity  	设置不透明度为0   IE9以前的版本   filter:Alpha(opacity=50)
	2、visibility 	设置元素是否可见   hidden
	3、display  	设置display none
	4、position  	定位到窗口之外   top:-999px;



元素居中
	1、通过绝对定位（元素的高度固定）
	2、flex