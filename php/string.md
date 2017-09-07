
function dump($soure){
	echo $soure.'<br/>';
}

/*
addcslashes() 函数返回在指定的字符前添加反斜杠的字符串
Hello \World!
 */
$str = addcslashes("Hello World!","W");
dump($str); 


/*
addslashes() 函数返回在预定义的字符前添加反斜杠的字符串。
预定义字符是：
单引号（'）
双引号（"）
反斜杠（\）
NULL
What does \"yolo\" mean?
 */
$str = addslashes('What does "yolo" mean?');
dump($str);


/*
bin2hex() 函数把 ASCII 字符的字符串转换为十六进制值
48656c6c6f20576f726c6421
 */
$str = bin2hex("Hello World!");
dump($str); 


/*
chop() 函数移除字符串右侧的空白字符或其他预定义字符。
Hello
 */
$str = "Hello World!";
 dump(chop($str,"World!"));


 /*
 explode() 函数使用一个字符串分割另一个字符串，并返回由字符串组成的数组
 第一个参数：分割的符号
 第二个参数：需要分割的字符串
 第三个参数：返回数组的数目
 ["2016","11","10"]
  */
 $date = "2016-11-10";
 $result = explode('-',$date);
 dump(json_encode($result));


 /*
 implode() 函数返回一个由数组元素组合成的字符串
 第一个参数：数组元素之间放置的内容，默认为“”
 第二个参数：数组
 Hello World php
  */
 $array = array('Hello','World','php');
dump(implode(' ',$array));


/*
join函数返回一个由数组元素组合成的字符串
第一个参数：数组元素之间放置的内容，默认为“”
第二个参数：数组
Hello World php
 */
 $array = array('Hello','World','php');
dump(join(' ',$array));

/*
lcfirst() 函数把字符串中的首字符转换为小写。
strtolower() 函数把字符串转换为小写。
strtoupper() - 把字符串转换为大写
ucfirst() - 把字符串中的首字符转换为大写
ucwords() - 把字符串中每个单词的首字符转换为大写
 */


/*
ltrim() 函数移除字符串左侧的空白字符或其他预定义字符。
rtrim() - 移除字符串右侧的空白字符或其他预定义字符。
trim() - 移除字符串两侧的空白字符或其他预定义字符。
 */


/*
md5()加密
e10adc3949ba59abbe56e057f20f883e
 */
dump(md5("123456"));

/*
md5_file() 函数计算文件的 MD5 散列
 */

/*
str_split() 函数把字符串分割到数组中。
["h","e","l","l","o"," ","w","o","r","l","d"," ","p","h","p"]
 */
$str = "hello world php";
dump(json_encode(str_split($str)));


/*
str_word_count() 函数计算字符串中的单词数。（不能区分中文）
3
 */
$str = "hello orld php";
dump(str_word_count($str));


/*
strlen() 函数返回字符串的长度。
14
 */
$str = "hello orld php";
dump(strlen($str));


/*
strtr() 函数转换字符串中特定的字符。
Hello World
 */
dump(strtr("Hilla Warld","ia","eo"));
