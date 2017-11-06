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




Grid布局（网格布局）
	术语：
		网格容器 ：元素应用display:grid的元素，他是所有网格项的父元素
		网格项：网格容器的直接子元素（第一级的子元素）
		网格线：组成网格线的分界线。它们可以是列网格线（column grid lines），也可以是行网格线（row grid lines）并且居于行或列的任意一侧
		网格轨道：两个相邻的网格线之间为网格轨道。你可以认为它们是网格的列或行
		网格单元：两个相邻的列网格线和两个相邻的行网格线组成的是网格单元
		网格区：网格区是由任意数量网格单元组成

	属性：
		display: grid | inline-grid | subgrid;
			grid: 生成块级网格
			inline-grid: 生成行内网格
			subgrid: 如果网格容器本身是网格项（嵌套网格容器），此属性用来继承其父网格容器的列、行大小
		注：当元素设置了网格布局，column、float、clear、vertical-align属性无效。
		
		grid-template-columns: <track-size> ... | <line-name> <track-size> ... ;
		grid-template-rows: <track-size> ... | <line-name> <track-size> ... ;
			设置行和列的大小，在行轨道或列轨道两边是网格线。
			track-size: 轨道大小，可以使用css长度，百分比或用分数（用fr单位）。
			line-name: 网格线名字，你可以选择任何名字



table布局
	table-layout：
		auto：默认的自动算法。（表格在每一单元格读取计算之后才会显示出来，速度很慢）
		fixed：固定布局的算法。（内容可能被裁切）
		设置或检索表格的布局算法。
		通常fixed算法会比auto算法高效，尤其是对于那些长表格来说。
		fixed算法使得表格可以像其它元素一样一行一行的渲染
	
	border-collapse：separate | collapse
		设置或检索表格的行和单元格的边是合并还是独立
			separate：边框独立
			collapse：相邻边被合并

	border-spacing
		设置或检索当表格边框独立时，行和单元格的边框在横向和纵向上的间距
	
	caption-side
			top：指定caption在表格上边
			bottom：指定caption在表格下边
		设置或检索表格的caption对象是在表格的那一边。

	empty-cells：hide | show
		设置或检索当表格的单元格无内容时，是否显示该单元格的边框。
			hide：指定当表格的单元格无内容时，隐藏该单元格的边框。
			show：指定当表格的单元格无内容时，显示该单元格的边框。


	
	
元素居中
	1、通过绝对定位
	2、flex




实现两栏布局有哪些方法
	1、通过设置宽度为50%，在设置浮动
	2、通过绝对定位设置和快读50%设置
	3、通过flex布局
	4、通过columns布局
	5、table布局
	6、grid布局