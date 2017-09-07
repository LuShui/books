Number.isFinite() 检查一个数值是否为有限的
        isFinite() 检查某个值是否为有限的
        两者的区别
            isFinite()会先进行数值的转换，在进行判断
            Number.isFinite()仅对数值有效，任何非数字的值都将返回false。

     Number.isNaN()用来检查一个值是否为NaN
        isNaN()用来检查一个值是否为NaN
        两者的区别
            isNan()会先进行数值的转换，在进行判断 例如isNaN('NaN') =》true
            Number.isNaN()只有对于NaN才返回true，非NaN一律返回false. Number.isNaN('NaN')=>false


     Number.parseInt(), Number.parseFloat()
        ES6将全局方法parseInt()和parseFloat()，移植到Number对象上面，行为完全保持不变

     Number.isInteger() 判断一个值是否为整数

     Number.EPSILON 新增的一个极小的常量
        Number.EPSILON
        // 2.220446049250313e-16
        Number.EPSILON.toFixed(20)
        // '0.00000000000000022204'

     Number.isSafeInteger() 安全整数
        JavaScript能够准确表示的整数范围在-2^53到2^53之间（不含两个端点），超过这个范围，无法精确表示这个值。
        ES6引入了Number.MAX_SAFE_INTEGER和Number.MIN_SAFE_INTEGER这两个常量，用来表示这个范围的上下限
        Number.MAX_SAFE_INTEGER === 9007199254740991 （备注：但是在控制台可以输出比这更大的数）
        Number.MIN_SAFE_INTEGER === -9007199254740991   （备注：但是在控制台可以输出比这更小的数）
            Number.isSafeInteger()用于判断值是否在这个区间之内