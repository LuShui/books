Array.from     
将两类对象转为真正的数组：
    类似数组的对象（array-like object）
    可遍历（iterable）的对象（包括ES6新增的数据结构Set和Map）
    只要是部署了Iterator接口的数据结构，Array.from都能将其转为数组
    如果参数是一个真正的数组，Array.from会返回一个一模一样的新数组
    类似数组的对象，本质特征只有一点，即必须有length属性。
        因此，任何有length属性的对象，都可以通过Array.from方法转为数组，而此时扩展运算符就无法转换
扩展运算符（...）也可以将某些数据结构转为数组
    扩展运算符背后调用的是遍历器接口（Symbol.iterator），如果一个对象没有部署这个接口，就无法转换

    let arguarr = {
        '0':1,'1':2,'2':3,'3':4,length:4
    };
    console.log(Array.from(arguarr));[1, 2, 3, 4]


Array.of      将一组值，转换为数组。
    这个方法的主要目的，是弥补数组构造函数Array()的不足。因为参数个数的不同，会导致Array()的行为有差异
    Array方法没有参数、一个参数、三个参数时，返回结果都不一样
    Array.of基本上可以用来替代Array()或new Array()，并且不存在由于参数不同而导致的重载。它的行为非常统一。
    Array.of总是返回参数值组成的数组。如果没有参数，就返回一个空数组
        Array.of() // []
        Array.of(undefined) // [undefined]
        Array.of(1) // [1]
        Array.of(1, 2) // [1, 2]


数组实例的find()和findIndex()
find()  找出第一个符合条件的数组成员。它的参数是一个回调函数，
        所有数组成员依次执行该回调函数，直到找出第一个返回值为true的成员，
        然后返回该成员。如果没有符合条件的成员，则返回undefined
        [1, 2, 3, 4].find(function(value, index, arr) {
            return value > 0;
        });

findIndex() 返回第一个符合条件的数组成员的位置，如果所有成员都不符合条件，则返回-1
        [1, 2, 3, 4].findIndex(function(value, index, arr) {
            return value > 0;
        });


fill()方法使用给定值，填充一个数组。数组中已有的元素，会被全部抹去
    ['a', 'b', 'c'].fill(7);// [7, 7, 7]
    new Array(3).fill(7); // [7, 7, 7]
fill方法还可以接受第二个和第三个参数，用于指定填充的起始位置和结束位置。


entries()，keys()和values()——用于遍历数组 它们都返回一个遍历器对象
    keys()是对键名的遍历
    values()是对键值的遍历
    entries()是对键值对的遍历
        for (let index of ['a', 'b'].keys()) {
            console.log(index);
        }// 0   1

        for (let elem of ['a', 'b'].values()) {
            console.log(elem);
        }// 'a'    'b'

        for (let [index, elem] of ['a', 'b'].entries()) {
            console.log(index, elem);
        } // 0 "a"    // 1 "b"


数组实例的includes()   返回一个布尔值，表示某个数组是否包含给定的值


