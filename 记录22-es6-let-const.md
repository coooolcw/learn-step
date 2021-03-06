
1.let
===
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/let  
  
let允许你声明一个作用域被限制在块级中的变量、语句或者表达式。  
与var关键字不同的是，var声明的变量只能是全局或者整个函数块的。  
  
注意点:  
1.在同一个作用域中用let重复定义一个变量将引起 TypeError.  
2.在 ECMAScript 2015 中，let 绑定不受变量提升的约束，这意味着 let  声明不会被提升到当前执行上下文的顶部。  
在块中的变量初始化之前，引用它将会导致 ReferenceError（而使用 var 声明变量则恰恰相反，该变量的值是 undefined ）。  
这个变量处于从块开始到 let 初始化处理的"暂存死区"之中。  
3.暂存死区  

```
        let foo = 1;
            function do_something() {
              console.log(bar); // undefined
              console.log(foo); // ReferenceError: foo is not defined 暂存死区
              var bar = 1;
              let foo = 2;
            }
```  
  
详细解释(实质上let也有类似于提升的行为,只是不同于var的提升)  
https://blog.csdn.net/A13330069275/article/details/81264890  

2.const
===
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/const  
  
常量,不可改变  
与var变量不同，全局常量不会变为窗口对象的属性。  
需要一个常数的初始化器,也就是说，必须在声明的同一语句中指定它的值。  
const声明创建一个值的只读引用。  
但这并不意味着它所持有的值是不可变的，只是变量标识符不能重新分配。  
例如，在引用内容是对象的情况下，这意味着可以改变对象的内容（例如，其参数）。  
关于“暂存死区”的所有讨论都适用于let和const。  
一个常量不能和它所在作用域内的其他变量或函数拥有相同的名称。  
    
可同时使用Object.freeze() 彻底冻结一个对象使该对象无法被修改  
作用目标为数组时,被冻结，其元素不能被修改。没有数组元素可以被添加或移除。  
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze  
  
无ES6的常量设置模拟  
===
方法1.假装  
变量大写假装不可修改  
  
2.Object.defineProperty()  
使用方法见  
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty  
红皮书p139开始  
  
在window上设置即可模仿全局常量  
  
当需要变为常量的是对象时,还同时需要使用Object.seal()  
Object.seal()方法封闭一个对象，阻止添加新属性并将所有现有属性标记为不可配置。当前属性的值只要可写就可以改变。   
  
简单封装的const引用类型的方法  
```
            Object.defineProperty(Object, 'noChange', {
                value: function(obj) {
                    for (var i in obj) {
                        if(obj.hasOwnProperty(i)) {
                            Object.defineProperty(obj, i, {
                                writable: false
                            });
                            if(obj[i] instanceof Object) {
                                Object.noChange(obj[i]);
                            }
                        }
                        Object.seal(obj);
                    }
                }
            });
```
