正则对象自由的方法以及属性

 test()
    返回一个布尔值，表示当前模式是否能匹配参数字符串。
    成功返回true，失败返回false

    let str = 'javascrip css and html';
    let result = /j/.test(str);
    console.log(result);//true


 exec()
    返回匹配结果。如果发现匹配，就返回一个数组，成员是每一个匹配成功的子字符串，否则返回null
    返回的结果集还包含index，和input属性
        input：整个原字符串。
        index：整个模式匹配成功的开始位置（从0开始计数）
    let str = 'javascrip css and html';
    let result = /j/.exec(str);
    console.log(result);//["j", index: 0, input: "javascrip css and html"]



 字符串的方法
     match()：返回一个数组，成员是所有匹配的子字符串。
     search()：按照给定的正则表达式进行搜索，返回一个整数，表示匹配开始的位置。如果没有则返回-1
     replace()：按照给定的正则表达式进行替换，返回替换后的字符串。
                接受两个参数，第一个是搜索模式，第二个是替换的内容
     split()：按照给定规则进行字符串分割，返回一个数组，包含分割后的各个成员


     match()
        let str = 'javascrip css and html';
        let result = str.match(/j|c/g);
        console.log(result);//["j", "c", "c"]

    search()
        let str = 'javascrip css and html';
        let result = str.search(/css/g);
        console.log(result);//10

    replace()
        let str = 'javascrip css and html';
        let result= str.replace(/css/g,'web');
        console.log(result);//javascrip web and html

   split()
        let str = 'javascrip css and html';
        let result= str.split(/s/);
        console.log(result);//["java", "crip c", "", " and html"]


   正则规则

   点字符（.)
        点字符（.）匹配除回车（\r）、换行(\n) 、行分隔符（\u2028）和段分隔符（\u2029）以外的所有字符
            let str = 'javascrip css and html';
            let result= str.split(/j.v/);
            console.log(result);//["", "ascrip css and html"]

 位置字符
    ^ 表示字符串的开始位置
        匹配是否已java开头
        let str = 'javascrip css and html';
        let result = /^java/.test(str);
        console.log(result);//true
    $ 表示字符串的结束位置
        匹配是否已html结尾
        let str = 'javascrip css and html';
        let result = /html$/.test(str);
        console.log(result);//true

 选择符（|）
    竖线符号（|）在正则表达式中表示“或关系”（OR）
    是否以html或者java开头
    let str = 'javascrip css and html';
    let result = /^html|^java/.test(str);
    console.log(result);//true

 字符类
 字符类（class）表示有一系列字符可供选择，只要匹配其中一个就可以了。所有可供选择的字符都放在方括号内
 匹配a,b,c中的一个
    let str = 'javascrip css and html';
    let result = /[abc]|^java/.test(str);
    console.log(result);//true

 如果方括号内的第一个字符是[^]，则表示除了字符类之中的字符，其他字符都可以匹配
 连字符（-）用来提供简写形式，表示字符的连续范围
 [0-9]表示0-9
 [a-z]表示字母a到z


 预定义匹配
 \d 匹配0-9之间的任一数字，相当于[0-9]。
 \D 匹配所有0-9以外的字符，相当于[^0-9]。
 \w 匹配任意的字母、数字和下划线，相当于[A-Za-z0-9_]。
 \W 除所有字母、数字和下划线以外的字符，相当于[^A-Za-z0-9_]。
 \s 匹配空格（包括制表符、空格符、断行符等），相等于[\t\r\n\v\f]。
 \S 匹配非空格的字符，相当于[^\t\r\n\v\f]。
 \b 匹配词的边界。
 \B 匹配非词边界，即在词的内部。


 重复类
    模式的精确匹配次数，
    使用大括号（{}）表示。
    {n}表示恰好重复n次，
    {n,}表示至少重复n次，
    {n,m}表示重复不少于n次，不多于m次。

 量词符
 量词符用来设定某个模式出现的次数。
    ? 问号表示某个模式出现0次或1次，等同于{0, 1}。
    * 星号表示某个模式出现0次或多次，等同于{0,}。
    + 加号表示某个模式出现1次或多次，等同于{1,}。


修饰符
 g：表示全局匹配
 i：表示忽略大小写