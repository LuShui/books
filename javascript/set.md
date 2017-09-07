    1、Set
     ES6 提供了新的数据结构 Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。
     Set 本身是一个构造函数，用来生成 Set 数据结构。
     Set 函数可以接受一个数组（或类似数组的对象）作为参数，用来初始化。
     Set 结构的实例有以下属性。
        Set.prototype.constructor：构造函数，默认就是Set函数。
        Set.prototype.size：返回Set实例的成员总数。
     Set操作方法。
        add(value)：添加某个值，返回Set结构本身。
        delete(value)：删除某个值，返回一个布尔值，表示删除是否成功。
        has(value)：返回一个布尔值，表示该值是否为Set的成员。
        clear()：清除所有成员，没有返回值。
     Set 遍历方法，可以用于遍历成员。(Set的遍历顺序就是插入顺序)
        keys()：返回键名的遍历器
        values()：返回键值的遍历器
        entries()：返回键值对的遍历器
        forEach()：使用回调函数遍历每个成员