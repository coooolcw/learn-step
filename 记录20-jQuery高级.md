
普通方法
---
设置class:block/none;
通过addClass  removeClass操作

jQ方法
---
操作display,以形变的方式消失/出现  
---
`.show([duration ] [, easing ] [, complete ])`  
`.hide([duration ] [, easing ] [, complete ])`  
`.toggle([duration ] [, easing ] [, complete ])`  

淡入淡出,修改透明度  
---
`.fadeIn( [duration ] [, easing ] [, complete ] )`  
`.fadeOut( [duration ] [, easing ] [, complete ] )`  
`.fadeToggle( [duration ] [, easing ] [, complete ] )`  


调整透明度  
---
`.fadeTo(duration, opacity [, easing ] [, complete ])`
        
单纯形变,修改高度  
---
`.slideDown( [duration ] [, easing ] [, complete ] )`  
`.slideUp( [duration ] [, easing ] [, complete ] )`  
`.slideToggle( [duration ] [, easing ] [, complete ] )`  
        
        
停止正在进行的动画 
---
`.stop( [queue ] [, clearQueue ] [, jumpToEnd ] )`  
clearQueue:true表示删除在队列中等待的其他动画  
jumpToEnd:一个布尔值指示是否当前动画立即完成  
  
`.finish( [queue ] )`  
停止当前正在运行的动画，删除所有排队的动画，并完成匹配元素所有的动画。  
  
stop与finish的区别  
`.finish()`方法和`.stop(true, true)`很相似,`.stop(true, true)`将清除队列,并且[目前]的动画跳转到其最终值.  
但是,不同的是,.finish() 会导致所有排队的动画的CSS属性跳转到他们的最终值.  

`jQuery.fx.off`  
当这个属性设置为true的时,调用时所有动画方法将立即设置元素为他们的最终状态,而不是显示效果.  
                
  
动画过渡插件  
---
jquery.easing  
https://github.com/gdsmith/jquery.easing  
效果查找站  
https://j11y.io/demos/jquery/easing/  
                
                
自定义动画
---
`.animate( properties [, duration ] [, easing ] [, complete ] )`  
类型: PlainObject  
一个CSS属性和值的对象,动画将根据这组对象移动。  
可进行+=运算,但需要用''包裹.无等号时可不需要  
`.animate( properties, options )`  
options 具体见https://www.html.cn/jqapi-1.9/animate/  
参考网站缺少了start的回调函数  
                                
                                
                                
jquery动画队列  
---
基础介绍  
https://blog.csdn.net/qq_42564846/article/details/81666008  
详细说明  
https://www.cnblogs.com/snandy/archive/2013/02/18/2892749.html   
`.queue()`  
`.queue( [queueName ] )`  
`.queue( [queueName ], newQueue )`  
`.queue( [queueName ], callback( next ) )`  
http://www.w3school.com.cn/jquery/data_queue.asp  
从jQuery 1.4开始，向队列中追加函数时，可以向该函数中传入另一个函数，作为第一个参数。  
当调用函数时，会自动从函数队列中弹出下一个项目，保证队列中函数的继续进行。我们可以像下面这样使用：  

```
$("#test").queue(function(next) {
  // Do some stuff...
  next();
});
```  

                        
`.dequeue( [queueName ] )`  
当.dequeue()被调用的时候，列队中的下一个函数将从这个列队中被移除，然后再执行。  
这个执行的函数中也应当直接或间接的包含 .dequeue()语句，这样才能继续执行队列中的其它函数，所以,这个序列可以继续。  
`.clearQueue( [queueName ] )`  
从列队中移除所有未执行的项。  
`.delay( duration [, queueName ] )`  
设置一个延时来推迟执行队列中后续的项。  
                        
  
jQ与其他插件共存
---
`jQuery.noConflict( [removeAll ] )`  
放弃jQuery控制$ 变量。  
旧引用的$ 被保存在jQuery的初始化; noConflict() 简单的恢复它们。(在引入冲突以后也可以消除冲突,并且复原其他插件)  
如果必要的话，我们可以释放jQuery名字，传递true作为一个参数给这个方法。` (var j = jQuery.noConflict();) ` 
但是大多数插件依靠jQuery存在的变量,这种情况下，可能导致插件不能正常操作。  

jQ兼容性判断  
---
`jQuery.support`  
但现在该属性已被放弃,建议使用Modernizr  
https://modernizr.com/  
                
修整字符串  
---
`jQuery.trim(str)`  
去掉字符串起始和结尾的空格。  

遍历  
---
`jQuery.each( collection, callback(indexInArray, valueOfElement) )`  
一个通用的迭代函数，它可以用来无缝迭代对象和数组。  
数组和类似数组的对象通过一个长度属性（如一个函数的参数对象）来迭代数字索引，从0到length - 1。  
其他对象通过其属性名进行迭代。  
`$.each()`函数和 `$(selector).each()`是不一样的，那个是专门用来遍历一个jQuery对象。  
`$.each()`函数可用于迭代任何集合，无论是“名/值”对象（JavaScript对象）或数组。  
在迭代数组的情况下，回调函数每次传递一个数组索引和相应的数组值作为参数。  
（该值也可以通过访问this关键字得到，但是JavaScript将始终将this值作为一个Object ，即使它是一个简单的字符串或数字值。）  
该方法返回其第一个参数，这是迭代的对象。  
可以在$.each()返回false来终止迭代。返回非false相当于一个循环中的continue语句，这意味着，它会立即跳出当前的迭代，转到下一个迭代。  

过滤数组
---
`jQuery.grep( array, function(elementOfArray, indexInArray) [, invert ] )`  
查找满足过滤函数的数组元素。原始数组不受影响。  
`$.grep()`方法会删除数组必要的元素，以使所有剩余元素通过过滤函数的检查。  
该测试是一个函数传递一个数组元素和该数组内这个的索引值。只有当测试返回true，该数组元素将返回到结果数组中。  
该过滤器的函数将被传递两个参数：当前正在被检查的数组中的元素，及该元素的索引值。  
该过滤器函数必须返回'true'以包含在结果数组项。  
function第一个参数是正在被检查的数组的元素，第二个参数是该元素的索引值。  
该函数应返回一个布尔值。this将是全局的window对象。  
  
转换数组/对象  
---
`jQuery.map( array, callback(elementOfArray, indexInArray) )`  
`jQuery.map( arrayOrObject, callback( value, indexOrKey ) )`  
`$.map()`方法会在数组的每一个元素或对象上应用一个函数并将结果映射到一个新的数组中。  
该函数可以返回：  
转换后的值，该值会被映射到最终的结果数组中  
null或者undefined, 用于移除该元素  
数组，会将该数组中的元素添加到最终的结果数组中(因此可使用split(),将数组中的字符串拆分成为一整个大数组)  

其他数组方法
---
`jQuery.inArray( value, array [, fromIndex ] )`  
在数组中查找指定值并返回它的索引（如果没有找到，则返回-1）.  
`jQuery.makeArray( obj )`  
转换一个类似数组的对象成为真正的JavaScript数组。  
`jQuery.merge( first, second )`  
合并两个数组内容到第一个数组。  

对象方法
---
`Query.extend( [deep ], target, object1 [, objectN ] )`  
将两个或更多对象的内容合并到第一个对象。  
deep  
如果是 true，合并成为递归（又叫做深拷贝）。不支持给这个参数传递 false.区别见  
https://www.html.cn/jqapi-1.9/jQuery.extend/  
当我们提供两个或多个对象给`$.extend()`，对象的所有属性都添加到目标对象（target参数）。  
如果只有一个参数提供给`$.extend()`，这意味着目标参数被省略。  
在这种情况下，jQuery对象本身被默认为目标对象。  
这样，我们可以在jQuery的命名空间下添加新的功能。  
这对于插件开发者希望向 jQuery 中添加新函数时是很有用的。  
  
判断类型  
---
`jQuery.isArray( obj )`  
确定的参数是一个数组。  
`jQuery.isEmptyObject( object )`  
检查对象是否为空（不包含任何属性）。  
`jQuery.isFunction( obj )`  
确定参数是否为一个Javascript 函数。  
`jQuery.isNumeric( value )`  
确定它的参数是否是一个JavaScript数字。  
`jQuery.isPlainObject( object )`  
测试对象是否是纯粹的对象（通过 "{}" 或者 "new Object" 创建的）  
`jQuery.isWindow( obj )`  
确定参数是否为一个window对象。  
  
`jQuery.type( obj )`  
确定JavaScript 对象的类型`[[Class]] `。  
较常用,具体见https://www.html.cn/jqapi-1.9/jQuery.type/  

其他方法
---
`jQuery.noop()`
当你仅仅想要传递一个空函数的时候，就用他吧。  
这对一些插件作者很有用，当插件提供了一个可选的回调函数接口，  
那么如果调用的时候没有传递这个回调函数，就用jQuery.noop来代替执行。  
  
`jQuery.contains( container, contained )`  
检查一个DOM元素是另一个DOM元素的后代。  
`jQuery.error( message )`  
接受一个字符串，并抛出包含这个字符串的异常。  
