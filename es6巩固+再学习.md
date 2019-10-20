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
