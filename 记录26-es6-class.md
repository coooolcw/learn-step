面向对象MDN  
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript  
  
MDN中的介绍,内容较为简单  
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Classes  
  
API参考  
ES6入门  
http://es6.ruanyifeng.com/#docs/class  
http://es6.ruanyifeng.com/#docs/class-extends  
  
深入理解ES6  
p181  
从早期的类模拟开始  
入门参考这本  
  
重点:    
===
1.constructor()和类基础  
---
类的所有方法都定义在类的prototype属性上面。  
在类的实例上面调用方法，其实就是调用原型上的方法.  
另外，类的内部所有定义的方法，都是不可枚举的  
  
  
constructor方法是类的默认方法，通过new命令生成对象实例时，自动调用该方法。  
一个类必须有constructor方法，如果没有显式定义，一个空的constructor方法会被默认添加。  
  
constructor方法默认返回实例对象（即this），完全可以指定返回另外一个对象。  
  
类必须使用new调用，否则会报错。这是它跟普通构造函数的一个主要区别，后者不用new也可以执行。  
  
  
2.静态方法和静态属性  
---
静态方法  
static  
类相当于实例的原型，所有在类中定义的方法，都会被实例继承。  
如果在一个方法前，加上static关键字，就表示该方法不会被实例继承，  
而是直接通过类来调用，这就称为“静态方法”。  
  
注意，如果静态方法包含this关键字，这个this指的是类，而不是实例。  
父类的静态方法，可以被子类继承。  
静态方法也是可以从super对象上调用的。  
  
静态属性  
静态属性指的是 Class 本身的属性，即Class.propName，而不是定义在实例对象（this）上的属性。  
```
class Foo {
}
Foo.prop = 1;
Foo.prop // 1
```
目前，只有这种写法可行，因为 ES6 明确规定，Class 内部只有静态方法，没有静态属性。  
现在有一个提案提供了类的静态属性，写法是在实例属性法的前面，加上static关键字。  
  
3.类表达式  
```
const person = class {
    //...
};
```
自执行  
```
const person = new class {
    //...
}();
```
4.get\/set  
---
与 ES5 一样，在“类”的内部可以使用get和set关键字，对某个属性设置存值函数和取值函数，拦截该属性的存取行为。  
```
class MyClass {
    constructor() {
        // ...
}
get prop() {
    return 'getter';
}
set prop(value) {
    console.log('setter: '+value);
    }
}
let inst = new MyClass();
inst.prop = 123;
// setter: 123
inst.prop
// 'getter'
```
5.(次要内容)name
---
name属性总是返回紧跟在class关键字后面的类名。  
若匿名则返回绑定的变量名  

6.new.target
---
new是从构造函数生成实例对象的命令。ES6 为new命令引入了一个new.target属性，  
该属性一般用在构造函数之中，返回new命令作用于的那个构造函数。  
如果构造函数不是通过new命令或Reflect.construct()调用的，new.target会返回undefined，  
因此这个属性可以用来确定构造函数是怎么调用的。  
  
7.es5的模拟类
---
代码见深入理解ES6 p184  
new的时候发生的事情  
https://www.cnblogs.com/joyco773/p/6480175.html  
创建一个空对象，作为将要返回的对象实例  
将这个空对象的原型，指向构造函数的 prototype 属性  
将这个空对象赋值给函数内部的 this 关键字  
开始执行构造函数内部的代码  
  
8.继承  
---
Class 可以通过extends关键字实现继承.  
子类必须在constructor方法中调用super方法，否则新建实例时会报错。  
这是因为子类自己的this对象，必须先通过父类的构造函数完成塑造，  
得到与父类同样的实例属性和方法，然后再对其进行加工，加上子类自己的实例属性和方法。  
如果不调用super方法，子类就得不到this对象。  
  
9.super
---
super这个关键字，既可以当作函数使用，也可以当作对象使用。在这两种情况下，它的用法完全不同。  
  
第一种情况，super作为函数调用时，代表父类的构造函数。ES6 要求，子类的构造函数必须执行一次super函数。  
作为函数时，super()只能用在子类的构造函数之中，用在其他地方就会报错。  
```
class A {}
class B extends A {
    constructor() {
        super();
    }
}
```
第二种情况，super作为对象时，在普通方法中，指向父类的原型对象；在静态方法中，指向父类。  
```
class A {
    p() {
        return 2;
    }
}
class B extends A {
    constructor() {
        super();
        console.log(super.p()); // 2
    }
}
let b = new B();
```
这里需要注意，由于super指向父类的原型对象，所以定义在父类实例上的方法或属性，是无法通过super调用的。  
如果属性定义在父类的原型对象上，super就可以取到。  
  
  
ES6 规定，在子类普通方法中通过super调用父类的方法时，方法内部的this指向当前的子类实例。  
由于this指向子类实例，所以如果通过super对某个属性赋值，这时super就是this，赋值的属性会变成子类实例的属性。  
  
  
如果super作为对象，用在静态方法之中，这时super将指向父类，而不是父类的原型对象。  
  
另外，在子类的静态方法中通过super调用父类的方法时，方法内部的this指向当前的子类，而不是子类的实例。  
  
  
注意，使用super的时候，必须显式指定是作为函数、还是作为对象使用，否则会报错。  
  
10.多态和重载
---
https://blog.csdn.net/weixin_40387601/article/details/80529351  
重载:函数参数类型不同行为不同  
多态:同名函数行为不同,js中基本只能使用class不同函数名相同来模拟  
多态的参考https://segmentfault.com/q/1010000003056336  
  
11.es5的继承
---
深入理解es6 p.196  
  
  
  
兼容  
===
babel插件  
https://babeljs.io/  
https://www.babeljs.cn/  
