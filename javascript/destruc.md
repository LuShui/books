    //最基本的实现
    let [a,b,c,d] = [1,2,3,4];// =>   a=1;b=2;c=3;d=4

    /*
    *   默认值
    *   ES6 内部使用严格相等运算符（===），判断一个位置是否有值。所以，如果一个数组成员不严格等于undefined，默认值是不会生效的
    */
    let [asp='asp'] = ['asd']; //=>  等价于以下代码
    /*
        let asp;
        if (['asd'][0] === undefined){
            asp = 'asp'; ['asd'][0];
        }else {
            asp = ['asd'][0];
        }
    */

    /**
     *  默认值可以引用解构赋值的其他变量，但该变量必须已经声明。
     *  若未声明，则会报引用错误（ReferenceError）
     *  * */
    let r;
    let [q=r,w=q,e=w]=[]; //q,w,e,r = undefined   声明但未赋值，所以结果为undefined

    //对象的解构复制           变量必须与属性同名，才能取到正确的值，否则取到的值undefined
    let {eat,fot,abc} = {
        eat:'eat',
        fot:'fot',
        hed:'hed'
    };//=> eat=eat;foot=fot;abc=undefined
    //如果变量名与属性名不一致
    let{eat:eat1,foot:fot1,hed:hed1} = {
        eat:'eat',
        fot:'fot',
        hed:'hed'
    };//=>eat1=eat;fot1=foot;hed1=hed
    //对象的解构赋值的内部机制，是先找到同名属性，然后再赋给对应的变量。真正被赋值的是后者，而不是前者。


    //字符串的解构赋值
    let [h,j,k,l,p]='hello';//=>h=h;j=e;k=l;l=l;p=o;
    let {length:len} = 'hello';//=>len=5;