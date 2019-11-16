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
不能直接参与运算  
主要用于对象属性名(注意不能使用点运算符读取symbol属性名的值)  
无法被普通方法遍历到(for...in,for...of,Object.keys(),Object.getOwnPropertyNames(),JSON.stringify())  
创建:  
1.symbol()  
symbol带参数时只是表示对当前Symbol值的描述,因此相同参数的Symbol函数的返回值是不相等的  
如果参数是一个对象,那就会先调用toString方法把对象变成字符串  
2.symbol.for()  
重点  
接受一个字符串作为参数,然后搜索有没有以该参数作为名称的Symbol值.如果有,就返回这个Symbol值,否则就新建并返回一个以该字符串为名称的Symbol值.  
  
  
遍历:  
1.遍历所有symbol属性Object.getOwnPropertySymbols  
2.遍历包括symbol的所有属性Reflect.ownKeys(obj)  

取值:
1.实例属性Symbol.prototype.description  
可取到`symbol()`或`symbol.for()`传入的数据  
返回描述  
  
2.Symbol.keyFor()返回一个已登记的symbol类型值的key  
Symbol.for(sym),返回注册时传入的数据(Symbol()或Symbol.for()传入的)  
  
10.set map
---
在数据存储结构中优先考虑Map、Set,适当放弃Array和Object  
[遍历方法和api等](http://es6.ruanyifeng.com/#docs/set-map)  
方法和api较多,查阅网站  
重点注意set,map与JSON格式的数据转换  
在需要临时存储DOM节点等信息时,可使用WeakSet以及WeakMap  
[一个什么时候使用Set Map结构的总结](https://medium.com/front-end-weekly/es6-map-vs-object-what-and-when-b80621932373)  
[中文翻译](https://juejin.im/post/5c7f6251f265da2dce1f68d3)  
  
使用...和new Set()/new Map()把set/map和数组相互转换,可使用所有数组方法  
  
WeakSet和WeakMap都只接受对象作为键,主要都用于DOM节点临时存储以及存储对象实例的私有数据.  
weak系列没有遍历,只能用add,delete,has方法.  
  
11.Proxy
---
内容较多  
proxy暂时使用频率较低,在需要使用的时候再查阅即可.  
vue3.0会在内部使用proxy跟踪数据变化,到时候可以学习  

技巧:将Proxy对象,设置到object.proxy属性,从而可以在object对象上调用  
`var object = { proxy: new Proxy(target, handler) };`  
  
reflect比较常用  
要把之前用Object调用的各种方法都替换成Reflect调用  
[api](http://es6.ruanyifeng.com/#docs/reflect)  
  
Proxy和Reflect的重点方法  
`get()` `set()` `apply()` `has()` `construct()` `ownKeys()`  
  
用途:  
解耦模块和业务,比如解耦校验模块与业务  
  
12.class
---
重要  
[内容见ES6入门](http://es6.ruanyifeng.com/#docs/class)  
注意:1.Class内定义的方法不可枚举,与ES5不同  
2.直接调用会报错  
3.默认严格模式  
4.没有变量提升  
5.在函数名前加\*代表是Generator方法  
6.注意this的指向  
7.属性后需要加`;`方法后不需要加`,`  
  
私有属性和方法:  
1.\_模拟  
2.Symbol模拟  
3.新提案,在属性/方法名前加#号,使用时也要带上#  

new.target方法判定是否是由new或Reflect.construct()调用,可用于function构造的类  
  
[Class继承](http://es6.ruanyifeng.com/#docs/class-extends)  
注意:  
1.子类必须在constructor方法中调用super方法,否则新建实例时会报错  
如果子类没有定义constructor方法,这个方法会被默认添加,并自动调用super  
2.在子类的构造函数中,只有调用super之后,才可以使用this关键字  
3.`super()`相当于`A.prototype.constructor.call(this)`  
4.作为函数,`super()`只能用在子类构造函数中,执行时,this指向的是子类  
5.super作为对象时,在普通方法中,指向父类的原型对象.在静态方法中,指向父类.  
6.在子类普通方法中通过super调用父类的方法时,方法内部的this指向当前的子类实例.  
7.通过super对某个属性赋,这时super就是this,赋值的属性会变成子类实例的属性  
8.super作为对象,用在静态方法之中,这时super将指向父类，而不是父类的原型对象  
9.在子类的静态方法中通过super调用父类的方法时,方法内部的this指向当前的子类,而不是子类的实例  
  
ES6可以继承原生构造函数,例如Number,Array  
13.Promise
---
重要  
Promise中如果不添加任何条件,直接调用resolve,与setTimeout设置为0类似,会在执行队列结束处添加resolve函数的调用  
node和游览器都有事件用于处理拒绝  
注意:
1.then返回一个新的Promise对象  
2.then中返回的参数会被下一个then传入回调函数  
3.then返回promise则下一个then会等待promise完成再进行调用  
4.reject()与throw Error作用类似  
5.
  
14.Iterator和for...of  
---
  
  
15.Generator
---
重点,难  
  
  
16.装饰器(decorator)
---
正在提案的第二阶段,尚未确定语法  
[github地址](https://github.com/tc39/proposal-decorators)  
  
17.Module
---
  
