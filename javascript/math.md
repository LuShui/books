    Math.trunc()   去除一个数的小数部分，返回整数部分
        Math.trunc(4.1) // 4
        Math.trunc(4.9) // 4
        Math.trunc(-4.1) // -4
        Math.trunc(-4.9) // -4
        Math.trunc(-0.1234) // -0
     非数值，Math.trunc内部使用Number方法将其先转为数值
     对于空值和无法截取整数的值，返回NaN


     Math.sign()    判断一个数到底是正数、负数、还是零。
        非数值，Math.sign()内部使用Number方法将其先转为数值
        它会返回五种值。
            参数为正数，返回+1；
            参数为负数，返回-1；
            参数为0，返回0；
            参数为-0，返回-0;
            其他值，返回NaN。

     Math.cbrt()    计算一个数的立方根。
        非数值，Math.cbrt()内部使用Number方法将其先转为数值

     Math.clz32方法返回一个数的32位无符号整数形式有多少个前导0
     Math.imul方法返回两个数以32位带符号整数形式相乘的结果
     Math.fround方法返回一个数的单精度浮点数形式


     Math.hypot方法返回所有参数的平方和的平方根
        如果参数不是数值，Math.hypot方法会将其转为数值。只要有一个参数无法转为数值，就会返回NaN。
        Math.hypot(3, 4);        // 5
        Math.hypot(-3);          // 3
        Math.hypot(3, 4, 'foo'); // NaN

     Math.signbit()方法判断一个数的符号位是否设置了。
        Math.signbit(2) //false
        Math.signbit(-2) //true
        Math.signbit(0) //false
        Math.signbit(-0) //true
        该方法的算法如下。
            如果参数是NaN，返回false
            如果参数是-0，返回true
            如果参数是负值，返回true
            其他情况返回false

     指数运算符 （**）
     ES2016 新增了一个指数运算符（**）
        2 ** 2 // 4
        2 ** 3 // 8
        指数运算符可以与等号结合，形成一个新的赋值运算符（**=）
            let a = 1.5;
            a **= 2;
            // 等同于 a = a * a;
            let b = 4;
            b **= 3;
            // 等同于 b = b * b * b;