mysql查询

	AND和OR可以混用，但AND比OR具有更高的优先级。如果你使用两个操作符，使用圆括号指明如何对条件进行分组

	NULL值操作
		判断值是否为NULL，不应该使用  =，<,>这些符号，应该使用IS NULL和IS NOT NULL操作符
		执行ORDER BY时，如果运行 ORDER BY ... ASC，则NULL值出现在最前面，若运行ORDER BY ... DESC，则NULL值出现在最后面