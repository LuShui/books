object相关
	克隆clone();
	浅克隆：只能克隆对象中的“非对象非资源”数据，否则会出现克隆不完全的现象。
	深克隆：需要使用__clone()方法


	class_exists(), ：判断某个类是否存在（定义过）
	interface_exists(), ：判断接口是否存在
	get_class()：获取某个对象的“所属类名”
	get_parent_class(), ：获取某个对象的“所属父类的类名”
	get_class_methods(), ：获取一个类的所有方法，返回一个索引数组，就是这些方法的名字。
	get_class_vars(), ：获取一个类的所有属性，返回一个数组，下标为属性名，值为属性值。
	get_declared_classes()：获得所有声明过的类（含系统中的类）
	is_object()：判断是否对象
	get_object_vars()：获得对象的所有属性，返回一个数组，下标为属性名，值为属性值
