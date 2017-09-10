1、PHP的作用域
	PHP 有四种不同的变量作用域
		1、local
		2、global
		3、static
		4、parameter

	局部和全局作用域
		在所有函数外部定义的变量，拥有全局作用域。除了函数外，全局变量可以被脚本中的任何部分访问，要在一个函数中访问一个全局变量，需要使用 global 关键字。(全局作用域不能再函数中访问)
		在 PHP 函数内部声明的变量是局部变量，仅能在函数内部访问
	
	global 关键字
		global 关键字用于函数内访问全局变量。在函数内调用函数外定义的全局变量，我们需要在函数中的变量前加上 global 关键字
	
	Static 作用域
		静态常量
	
	参数作用域
		过调用代码将值传递给函数的局部变量。参数是在参数列表中声明的，作为函数声明的一部分


2、文件包含
	include，include_once 和 require,require_once
	
	include 和 require除了处理错误的方式不同之外，在其他方面都是相同的
		require 生成一个致命错误（E_COMPILE_ERROR），在错误发生后脚本会停止执行。
		include 生成一个警告（E_WARNING），在错误发生后脚本会继续执行。

	include和require 重复导入同一个文件会多次重复的导入。
	include_once和require_once 只会导入一次文件。


3、变量和常量
	1、php中变量默认都是值传递。

	常量定义
		1、通过define()定义。可以再任意的位置定义。
		2、通过conset定义。必须定义在最外外层的作用域中。不能再函数内定义

	常量的使用
		1、直接通过定义的名字使用。
		2、通过constant()函数使用。


4、





	
