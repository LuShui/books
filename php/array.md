/*
数组初始化
 */
function dump($soure){
	echo json_encode($soure);
}

$array = array(1,2,3,4,5);
dump($array);


/**
  array_change_key_case()array_change_key_case 将数组的所有的键都转换为大写字母或小写字母
  {"CODE":"code","AGE":10,"NAME":"php"}
 */
$array = array(
	'code'=>'code',
	'age'=>10,
	'name'=>'php'
	);
dump(array_change_key_case($array,CASE_UPPER));


/*
array_chunk()把一个数组分割为新的数组块
[["code",10],["php"]]
 */
$array = array(
	'code'=>'code',
	'age'=>10,
	'name'=>'php'
	);
dump(array_chunk($array, 2));

/*
array_column() 返回输入数组中某个单一列的值。
目标数组需要时一个二维数组
{"php":10}
 */
$array = array(
	'name'=>array(
		'code'=>'code',
		'age'=>10,
		'name'=>'php'
	)
);

dump(array_column($array,'age','name'));


/*
array_combine() 函数通过合并两个数组来创建一个新数组，其中的一个数组元素为键名，另一个数组的元素为键值。
键名数组和键值数组的元素个数必须相同且键值的顺序一一对应
{"name":"php","age":"1","code":10}
 */
$key = array('name','age','code');
$value = array('php','1',10);
dump(array_combine($key,$value));


/*
array_count_values() 统计数组中所有值出现的次数
 {"codevalue":1,"10":1,"phpvalue":1}
 */
$array = array(
	'code'=>'codevalue',
	'age'=>10,
	'name'=>'phpvalue'
	);
dump(array_count_values($array));


/*
array_fill() 函数用给定的键值填充数组
{"3":"php","4":"php"}
 */
dump(array_fill(3,2,'php'));


/*
array_fill_keys() 函数用给定的指定键名的键值填充数组。
 {"a":"red","b":"red","c":"red"}
 */
$keys = array('a','b','c');
dump(array_fill_keys($keys,'red'));

/*
array_filter() 函数用回调函数过滤数组中的元素
[1,2,3,4,5,6,7]
 */
$array = array(1,2,3,4,5,6,7);
dump(array_filter($array,function($value){
	return $value;
}));

/*
array_flip() 函数用于反转/交换数组中的键名和对应关联的键值
{"codevalue":"code","10":"age","phpvalue":"name"}
 */
$array = array(
	'code'=>'codevalue',
	'age'=>10,
	'name'=>'phpvalue'
	);
dump(array_flip($array));


/*
array_key_exists() 函数检查某个数组中是否存在指定的键名，如果键名存在则返回 true，如果键名不存在则返回 false。
true
 */
$array = array(
	'code'=>'codevalue',
	'age'=>10,
	'name'=>'phpvalue'
	);
dump(array_key_exists('age',$array));


/*
array_keys() 函数返回包含数组中所有键名的一个新数组
 ["code","age","name"]
 */
$array = array(
	'code'=>'codevalue',
	'age'=>10,
	'name'=>'phpvalue'
	);
dump(array_keys($array));

/*
array_map() 数组遍历，返回回调函数操作后的值
[1,4,9,16]
 */
$array = array(1,2,3,4);
dump(array_map(function($val){
	return $val * $val;
},$array));


/*
array_merge() 函数用于把一个或多个数组合并为一个数组
相同的键名，最后的元素会覆盖其他元素
{"a":"red","b":"yellow","c":"blue"}
 */
$a1=array("a"=>"red","b"=>"green");
$a2=array("c"=>"blue","b"=>"yellow");
dump(array_merge($a1,$a2));


/*
array_merge_recursive() 函数用于把一个或多个数组合并为一个数组
相同的键名将多个相同键名的值递归组成一个数组
{"a":"red","b":["green","yellow"],"c":"blue"}
 */
$a1=array("a"=>"red","b"=>"green");
$a2=array("c"=>"blue","b"=>"yellow");
dump(array_merge_recursive($a1,$a2));


/*
array_pop() 函数删除数组中的最后一个元素
返回被删除的元素
8
 */
$array = array(1,2,3,4,8);
dump(array_pop($array));


/*
array_product() 函数计算并返回数组的乘积。
120
 */
$array = array(1,2,3,4,5);
dump(array_product($array));


/*
array_push() 函数向数组尾部插入一个或多个元素。
返回新数组的元素个数
8
 */
$array = array(1,2,3,4,5);
dump(array_push($array,7,9,11));


/*
array_rand() 函数返回数组中的一个随机键名，或者如果指定函数返回键名不只一个，则返回一个包含随机键名的数组
 */
$array = array(
	'code'=>'codevalue',
	'age'=>10,
	'name'=>'phpvalue'
	);
dump(array_rand($array));


/*
array_reduce() 遍历数组，数组转字符串
codevalue10phpvalu
 */
$array = array(
	'code'=>'codevalue',
	'age'=>10,
	'name'=>'phpvalue'
	);
dump(array_reduce($array,function($value1,$value2){
	return $value1 . $value2;
}));


/*
array_replace() 函数使用后面数组的值替换第一个数组的值
["one","two",3]
 */
$array1 = array(1,2,3);
$array2 = array('one','two');
dump(array_replace($array1,$array2));


/*
array_reverse() 函数返回翻转顺序的数组
{"name":"phpvalue","age":10,"code":"codevalue"}
 */
$array = array(
	'code'=>'codevalue',
	'age'=>10,
	'name'=>'phpvalue'
	);
dump(array_reverse($array));


/*
array_search() 函数在数组中搜索某个键值，并返回对应的键名
3
 */
$array = array(
	array(
		'name'=>'php'
	),
	array(
		'name'=>'html'
	),
	array(
		'name'=>'js'
	),
	array(
		'name'=>'css'
	)
);
$a = $array[3];
dump(array_search($a,$array));


/*
array_shift() 函数用于删除数组中的第一个元素，并返回被删除的元素
codevalue
 */
$array = array(
	'code'=>'codevalue',
	'age'=>10,
	'name'=>'phpvalue'
	);
dump(array_shift($array));


/*
array_slice() 函数返回数组中的选定部分。
{"age":10,"name":"phpvalue"}
 */
$array = array(
	'code'=>'codevalue',
	'age'=>10,
	'name'=>'phpvalue'
	);
dump(array_slice($array,1,2));


/*
array_unique() 函数用于移除数组中重复的值。如果两个或更多个数组值相同，只保留第一个值，其他的值被移除
 */
$array = array(
	'code'=>'codevalue',
	'age1'=>10,
	'age2'=>20,
	'age3'=>30,
	'name'=>'phpvalue'
	);
dump(array_unique($array));


/*
array_unshift() 函数用于向数组插入新元素。新数组的值将被插入到数组的开头
7
{"0":20,"1":50,"code":"codevalue","age1":10,"age2":20,"age3":30,"name":"phpvalue"}
 */

$array = array(
	'code'=>'codevalue',
	'age1'=>10,
	'age2'=>20,
	'age3'=>30,
	'name'=>'phpvalue'
	);
dump(array_unshift($array,20,50));
dump($array);


/*
array_values() 函数返回包含数组中所有的值的数组
["codevalue",10,20,30,"phpvalue"]
 */
$array = array(
	'code'=>'codevalue',
	'age1'=>10,
	'age2'=>20,
	'age3'=>30,
	'name'=>'phpvalue'
	);
dump(array_values($array));


/*
arsort() 函数对关联数组按照键值进行降序排序。
{"age3":30,"age2":20,"age1":10,"name":"phpvalue","code":"codevalue"}
 */
$array = array(
	'code'=>'codevalue',
	'age1'=>10,
	'age2'=>20,
	'age3'=>30,
	'name'=>'phpvalue'
	);
arsort($array);
dump($array);

/*
count() 函数返回数组中元素的数目。
5
 */
dump(count($array));

/*
current() 函数返回数组中的当前元素的值
 */
dump(current($array));


