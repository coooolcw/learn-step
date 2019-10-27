http://es6.ruanyifeng.com/  
辅助的书  
  
1.let const  
===
块级作用域(略)  
  
es6模块自动采用严格模式
  
const对于对象的修改,以及冻结对象

2.解构赋值  
===
数组解构赋值  
对象解构赋值  
默认值  
变量名  

常用:  
变量交换  
接收函数返回值  
JSON  
  
注意点:函数如果解构一个传入的对象,比如给这个对象设置默认值,即
```
function move({x = 0, y = 0} = {}) {
  return [x, y];
}
```  
中的` = {}`  
否则不传入这个值就会报错(undefined作为对象解构报错)  
另:模式语句中不要使用`()`  
  
3.正则扩展  
===
构造函数的变化  
y修饰符以及sticky属性  
u修饰符用于处理大于`\uFFFF`的字符  
unicode属性  
flags属性  
s修饰符  
  
4.字符串扩展  
===
unicode表示法`u{}`  
遍历器接口`for of`  
实例方法codePointAt()  
实例方法includes()  startsWith() endsWith()  
实例方法repeat()  
实例方法padStart()  padEnd()
String.fromCodePoint()   
String.raw()  
注意使用的时候是
```
String.raw`字符串`
```  
模板字符串  
模板编译  有点难,用于vue,react等模板处理  
标签模板  重要  常用于防止XSS攻击,多国语言模板处理  
  
5.数值扩展
===
二进制和八进制(0b 0o)  
转换回十进制则用`Number('')`;  
不太常用的API`Number.isFinite()`&`Number.isNaN()`  
常用API  
`Number.isInteger()`注意15.0也视为整数,传入非数字返回false,同时数据精度可能会造成误判  
[详情](http://es6.ruanyifeng.com/#docs/number)  
数字上下限  
`Number.MAX_SAFE_INTEGER`和`Number.MIN_SAFE_INTEGER`  
`Number.isSafeInteger()`判断是否在这个范围之内  
  
`Math.trunc()`去除一个数的小数部分,返回整数部分,不进行四舍五入等操作  
`Math.sign()`判断一个数到底是正数、负数、还是零,若参数为非数值,会先将其转换为数值  
[具体返回的规则](http://es6.ruanyifeng.com/#docs/number#Math-sign)  
`Math.cbrt()`计算一个数的立方根  
  
6.数组扩展
===
`Array.of()`将一组值,转换为数组,用于替代`new Array()`和`Array()`  
`Array.of()`总是返回参数值组成的数组.如果没有参数,就返回一个空数组.  
`Array.from()`将两类对象转为真正的数组:类似数组的对象(array-like object)和可遍历(iterable)的对象  
常用于把querySelectorAll返回的类数组转为真正的数组  
`Array.from`还可以接受第二个参数,作用类似于数组的map方法,用来对每个元素进行处理,将处理后的值放入返回的数组.  
还用于将字符串转为数组,然后返回字符串的正确长度,防止大于\uFFFF的字符计算成两个字符  
实例方法fill(),使用给定值,填充一个数组.注意如果填充物是一个对象,不会进行深拷贝,拷贝的是同一个指针  
  
实例方法`entries()`,`keys()`和`values()`——用于遍历数组  
它们都返回一个遍历器对象,可以用`for...of`循环进行遍历,`keys()`是对键名的遍历,`values()`是对键值的遍历,`entries()`是对键值对的遍历  
  
实例方法`copyWithin()`.在当前数组内部,将指定位置的成员复制到其他位置(会覆盖原有成员),然后返回当前数组.会修改现有数组  
  
实例方法`find()`,`findIndex()`  
find它的参数是一个回调函数,所有数组成员依次执行该回调函数,直到找出第一个返回值为true的成员.  
findIndex返回返回第一个符合条件的数组成员的位置，如果所有成员都不符合条件，则返回-1  
这两个方法都可以接受第二个参数,用来绑定回调函数的this对象  
这两个方法都可以发现NaN  
  
实例方法`includes()`  
方法返回一个布尔值,表示某个数组是否包含给定的值  
该方法的第二个参数表示搜索的起始位置,默认为0.如果第二个参数为负数,则表示倒数的位置  
  
7.函数扩展
===
默认值 重点  
注意点:1.惰性求值,每次使用时(运行时)计算设定的默认表达式的值  
2.例子  
```
function foo({x, y = 5} = {}) {
  console.log(x, y);
}

foo() // undefined 5
```
不设置`= {}`的话不传入对象就没有默认值  
3.通常情况下,定义了默认值的参数,应该是函数的尾参数  
4.指定了默认值以后,函数的length属性,将返回没有指定默认值的参数个数.也就是length属性会失真
5.函数进行声明初始化时,参数会形成一个单独的作用域(context).等到初始化结束,这个作用域就会消失
类似包裹在函数内部作用域外层的作用域,但也不是全局作用域.
  
rest参数  
获取函数的多余参数,这样就不需要使用arguments对象了
  
箭头函数  
重点  
注意点:1.this不同,箭头函数this在定义时确定,不是运行时的对象,也就是没有自己的this  
2.不能用new  
3.没有arguments对象  
4.不能使用yield  
  
尾调用  
用于优化递归性能,在需要性能优化的时候使用.  
内容较多,较难  
[详情](http://es6.ruanyifeng.com/#docs/function#%E5%B0%BE%E8%B0%83%E7%94%A8%E4%BC%98%E5%8C%96)  
  
8.对象扩展
===
简洁表示法  
常用  
属性和方法的简洁表示  
  
属性名表达式  
```
let propKey = 'foo';

let obj = {
  [propKey]: true,
  ['a' + 'bc']: 123
};
```
  
`Object.is()`用来比较两个值是否严格相等,与严格比较运算符(===)的行为基本一致,除了NaN与+0-0,NaN与NaN返回true,+0 -0返回false.  
`Object.assign`用于对象的合并，将源对象(source)的所有可枚举属性，复制到目标对象(target)  
注意:  
1.浅拷贝  
2.同名属性替换  
3.可处理数组,但是会把数组当做object  
4.不会复制函数体,只会复制函数的返回值(如果返回的是值的话)  
`Object.keys``Object.values``Object.entries`常用的是entries  
  
  
9.symbol
---
新的数据类型  
  
