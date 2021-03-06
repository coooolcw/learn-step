官网  
vue官方文档  
https://cn.vuejs.org/  
vue-cli  
https://cli.vuejs.org/zh/  
cli3的配置参考  
https://cli.vuejs.org/zh/config/  
  
vue3对于vue2的目录结构有较大的改动  
但是会替代vue2 因此直接参考vue3 cli 的官方文档   
  
  
学习历程  
1.基础用法  
直接在html中引入  
`<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>`
  
vue学习  
1.创建实例  
---
略  
  
2.data数据绑定☆  
---
注意点:只有当实例被创建时 data 中存在的属性才是响应式的  
  
3.vue实例方法  
---
https://cn.vuejs.org/v2/api/#%E5%AE%9E%E4%BE%8B%E5%B1%9E%E6%80%A7  
待使用一段时间后补充常用方法  
  
4.生命周期钩子  
---
生命周期图示https://cn.vuejs.org/v2/guide/instance.html#%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E5%9B%BE%E7%A4%BA  
重要的时间点  
mounted  
如果 root 实例挂载了一个文档内元素，当 mounted 被调用时 vm.$el 也在文档内。  
注意:该钩子在服务器端渲染期间不被调用。  
  
注意:不要在选项属性或回调上使用箭头函数，比如 `created: () => console.log(this.a)` 或  
`vm.$watch('a', newValue => this.myMethod())`。  
箭头函数并没有 this，this 会作为变量一直向上级词法作用域查找，直至找到为止，  
经常导致 `Uncaught TypeError: Cannot read property of undefined` 或   
`Uncaught TypeError: this.myMethod is not a function` 之类的错误。  
  
5.模板语法☆  
---
文本  
指令  
v-html v-bind v-on  
v-html  
双大括号会将数据解释为普通文本，而非 HTML 代码。为了输出真正的 HTML，你需要使用 v-html 指令  
`v-html="rawHtml"`  
注意:1.变量的值会直接作为HTML,忽略解析属性值中的数据绑定.  
2.你不能使用 v-html 来复合局部模板  
  
v-bind  
Mustache 语法不能作用在 HTML 特性上，遇到这种情况应该使用 v-bind 指令  
`<div v-bind:id="dynamicId"></div>`  
对于布尔特性 (它们只要存在就意味着值为 true)，v-bind 工作起来略有不同,  
`<button v-bind:disabled="isButtonDisabled">Button</button>`  
如果 isButtonDisabled 的值是 null、undefined 或 false，  
则 disabled 特性甚至不会被包含在渲染出来的 <button> 元素中。  
  
v-on  
  
  
js表达式  
重点:1.if语句不生效,必须使用三元表达式  
2.模板表达式都被放在沙盒中，只能访问全局变量的一个白名单，如 Math 和 Date  
  
动态参数☆  
可以用方括号括起来的 JavaScript 表达式作为一个指令的参数  
动态参数预期会求出一个字符串，异常情况下值为 null。这个特殊的 null 值可以被显性地用于移除绑定。  
任何其它非字符串类型的值都将会触发一个警告。  
动态参数表达式有一些语法约束，因为某些字符，例如空格和引号，放在 HTML 特性名里是无效的。  
同样，在 DOM 中使用模板时你需要回避大写键名。  
  
修饰符☆  
修饰符 (modifier) 是以半角句号 . 指明的特殊后缀，用于指出一个指令应该以特殊方式绑定。  
例:.prevent 修饰符告诉 v-on 指令对于触发的事件调用 event.preventDefault()  
  
  
6.计算属性☆  
---
https://cn.vuejs.org/v2/guide/computed.html  
模板内的表达式非常便利，但是设计它们的初衷是用于简单运算的。在模板中放入太多的逻辑会让模板过重且难以维护。  
对于任何复杂逻辑，都应当使用计算属性  
例子见https://cn.vuejs.org/v2/guide/computed.html#%E5%9F%BA%E7%A1%80%E4%BE%8B%E5%AD%90  
  
vs方法  
我们可以将同一函数定义为一个方法而不是一个计算属性。  
两种方式的最终结果确实是完全相同的。  
然而，不同的是计算属性是基于它们的响应式依赖进行缓存的。  
只在相关响应式依赖发生改变时它们才会重新求值。  
这就意味着只要 message 还没有发生改变，  
多次访问 reversedMessage 计算属性会立即返回之前的计算结果，而不必再次执行函数。  
  
相比之下，每当触发重新渲染时，调用方法将总会再次执行函数  
  
侦听☆  
常用于需要ajax的数据改变  
https://cn.vuejs.org/v2/guide/computed.html#%E4%BE%A6%E5%90%AC%E5%99%A8  
watch的api  
https://cn.vuejs.org/v2/api/#watch  
  
setter  
计算属性默认只有 getter ，不过在需要时你也可以提供一个 setter  
赋值vm.变量时会调用setter  
  
7.Class 与 Style 绑定  
===
class  
对象语法  
绑定的数据对象不必内联定义在模板里  
也可以在这里绑定一个返回对象的计算属性。  
数组语法  
在数组语法中也可以使用对象语法  
`<div v-bind:class="[{ active: isActive }, errorClass]"></div>`  
在组件上使用  
https://cn.vuejs.org/v2/guide/class-and-style.html#%E7%94%A8%E5%9C%A8%E7%BB%84%E4%BB%B6%E4%B8%8A  
暂缓  
style  
对象语法  
直接绑定到一个样式对象通常更好,同样的，对象语法常常结合返回对象的计算属性使用。  
数组语法  
v-bind:style 的数组语法可以将多个样式对象应用到同一个元素上  
注意:这里与class不同,只能使用样式对象  
`<div v-bind:style="[baseStyles, overridingStyles]"></div>`  
`baseStyles = { color : red}`  
  
多重值  
`<div :style="{ display: ['-webkit-box', '-ms-flexbox', 'flex'] }"></div>`  
这样写只会渲染数组中最后一个被浏览器支持的值。  
在本例中，如果浏览器支持不带浏览器前缀的 flexbox，那么就只会渲染 display: flex。  
  
8.条件渲染  
===
v-if  
v-if 指令用于条件性地渲染一块内容。这块内容只会在指令的表达式返回 truthy 值的时候被渲染。  
可以把一个 <template> 元素当做不可见的包裹元素，并在上面使用 v-if。最终的渲染结果将不包含 <template> 元素。  
v-else  
你可以使用 v-else 指令来表示 v-if 的“else 块”  
v-else-if  
v-else-if，顾名思义，充当 v-if 的“else-if 块”，可以连续使用.  
类似于 v-else，v-else-if 也必须紧跟在带 v-if 或者 v-else-if 的元素之后.  
  
用key管理元素  
Vue 会尽可能高效地渲染元素，通常会复用已有元素而不是从头开始渲染。  
添加一个具有唯一值的 key 属性即可表达“这两个元素是完全独立的，不要复用它们”.  
  
v-show  
另一个用于根据条件展示元素的选项是 v-show 指令.  
不同的是带有 v-show 的元素始终会被渲染并保留在 DOM 中。v-show 只是简单地切换元素的 CSS 属性 display。  
注意:  
v-show 不支持 <template> 元素，也不支持 v-else。  
  
v-if vs v-show  
一般来说，v-if 有更高的切换开销，而 v-show 有更高的初始渲染开销。  
因此，如果需要非常频繁地切换，则使用 v-show 较好；如果在运行时条件很少改变，则使用 v-if 较好。  
  
注意:不推荐同时使用 v-if 和 v-for  
  
9.列表渲染  
v-for  
数组  
我们可以用 v-for 指令基于一个数组来渲染一个列表。  
v-for 指令需要使用 item in items 形式的特殊语法，其中 items 是源数据数组，而 item 则是被迭代的数组元素的别名.  
  
在 v-for 块中，我们可以访问所有父作用域的属性。v-for 还支持一个可选的第二个参数，即当前项的索引。  
你也可以用 of 替代 in 作为分隔符，因为它更接近 JavaScript 迭代器的语法  
  
对象  
你也可以用 v-for 来遍历一个对象的属性。  
你也可以提供第二个的参数为 property 名称 (也就是键名)  
在遍历对象时，会按 Object.keys() 的结果遍历，但是不能保证它的结果在不同的 JavaScript 引擎下都一致。  
因此index不能作为判断基准  
更新/维护状态  
当 Vue 正在更新使用 v-for 渲染的元素列表时，它默认使用“就地更新”的策略。  
如果数据项的顺序被改变，Vue 将不会移动 DOM 元素来匹配数据项的顺序，而是就地更新每个元素，  
并且确保它们在每个索引位置正确渲染。  
这个默认的模式是高效的，但是只适用于不依赖子组件状态或临时 DOM 状态 (例如：表单输入值) 的列表渲染输出。  
为了给 Vue 一个提示，以便它能跟踪每个节点的身份，从而重用和重新排序现有元素，你需要为每项提供一个唯一 key 属性  
```
<div v-for="item in items" v-bind:key="item.id">
<!-- 内容 -->
</div>
```
建议尽可能在使用 v-for 时提供 key attribute，除非遍历输出的 DOM 内容非常简单，  
或者是刻意依赖默认行为以获取性能上的提升。  
更新检测  
https://cn.vuejs.org/v2/guide/list.html#%E6%95%B0%E7%BB%84%E6%9B%B4%E6%96%B0%E6%A3%80%E6%B5%8B  
注意:  
数组  
由于 JavaScript 的限制，Vue 不能检测以下数组的变动  
1.当你利用索引直接设置一个数组项时  
2.当你修改数组的长度时  
解决方法:  
1.set方法  
2.splice方法  
方法  
Vue 不能检测对象属性的添加或删除  
对于已经创建的实例，Vue 不允许动态添加根级别的响应式属性。  
但是，可以使用 `Vue.set(object, propertyName, value)` 方法向嵌套对象添加响应式属性。  
还可以使用 `vm.$set` 实例方法，它只是全局 `Vue.set` 的别名  
  
有时你可能需要为已有对象赋值多个新属性，比如使用 `Object.assign()` 或 `_.extend()`。  
在这种情况下，你应该用两个对象的属性创建一个新的对象。  
显示过滤/排序后的结果  
有时，我们想要显示一个数组经过过滤或排序后的版本，而不实际改变或重置原始数据。  
在这种情况下，可以创建一个计算属性，来返回过滤或排序后的数组。  
  
在 v-for 里使用值范围  
v-for 也可以接受整数。在这种情况下，它会把模板重复对应次数。item的值取第n-1次  
  
10.事件处理
===
v-on
可以用 v-on 指令监听 DOM 事件，并在触发时运行一些 JavaScript 代码。  
v-on 还可以接收一个需要调用的方法名称。  
除了直接绑定到一个方法，也可以在内联 JavaScript 语句中调用方法.  
有时也需要在内联语句处理器中访问原始的 DOM 事件。可以用特殊变量 $event 把它传入方法  
  
事件修饰符☆  
https://cn.vuejs.org/v2/guide/events.html#%E4%BA%8B%E4%BB%B6%E4%BF%AE%E9%A5%B0%E7%AC%A6  
重点:使用修饰符时，顺序很重要；相应的代码会以同样的顺序产生。  
因此，用 v-on:click.prevent.self 会阻止所有的点击，而 v-on:click.self.prevent 只会阻止对元素自身的点击。  
  
按键修饰符☆  
我们经常需要检查详细的按键。Vue 允许为 v-on 在监听键盘事件时添加按键修饰符  
你可以直接将 KeyboardEvent.key 暴露的任意有效按键名转换为 kebab-case 来作为修饰符  
`<input v-on:keyup.page-down="onPageDown">`  
  
可以用如下修饰符来实现仅在按下相应按键时才触发鼠标或键盘事件的监听器。  
.ctrl  
.alt  
.shift  
.meta  
注意:  
请注意修饰键与常规按键不同，在和 keyup 事件一起用时，事件触发时修饰键必须处于按下状态。  
换句话说，只有在按住 ctrl 的情况下释放其它按键，才能触发 keyup.ctrl。  
而单单释放 ctrl 也不会触发事件。如果你想要这样的行为，请为 ctrl 换用 keyCode：keyup.17。  
.exact 修饰符允许你控制由精确的系统修饰符组合触发的事件。  
.left.right.middle这些修饰符会限制处理函数仅响应特定的鼠标按钮。  
  
11.表单输入绑定
===
https://cn.vuejs.org/v2/guide/forms.html  
v-model  
v-model 指令在表单 <input>、<textarea> 及 <select> 元素上创建双向数据绑定.  
注意点:  
1.v-model 会忽略所有表单元素的 value、checked、selected 特性的初始值而总是将 Vue 实例的数据作为数据来源。  
你应该通过 JavaScript 在组件的 data 选项中声明初始值。  
2.v-model 在内部为不同的输入元素使用不同的属性并抛出不同的事件：  
text 和 textarea 元素使用 value 属性和 input 事件；  
checkbox 和 radio 使用 checked 属性和 change 事件；  
select 字段将 value 作为 prop 并将 change 作为事件。  
3.对于需要使用输入法 (如中文、日文、韩文等) 的语言，你会发现 v-model 不会在输入法组合文字过程中得到更新。  
4.在文本区域插值(`<textarea>{{text}}</textarea>`)并不会生效，应用 v-model 来代替。  
5.多选框会根据选择的顺序push值(checkbox)  
6.如果 v-model 表达式的初始值未能匹配任何选项，<select> 元素将被渲染为“未选中”状态。  
在 iOS 中，这会使用户无法选择第一个选项。因为这样的情况下，iOS 不会触发 change 事件。  
更推荐在第一个位置提供一个值为空的禁用选项。  
7.select多选时会根据设定内容的顺序填充数组,而不是选择的顺序push  
8.可与v-for搭配使用  
值的绑定  
https://cn.vuejs.org/v2/guide/forms.html#%E5%80%BC%E7%BB%91%E5%AE%9A  
难以概括,参见官网  
主要:v-bind:value  
修饰符  
.lazy.number.trim  
  
12.组件基础  
===
https://cn.vuejs.org/v2/guide/components.html  
重要概念:https://wiki.imooc.com/vue/vuejscomponent.html  
内容较多,仅摘要  
重点:  
1.一个组件的 data 选项必须是一个函数，因此每个实例可以维护一份被返回对象的独立的拷贝  
2.有两种组件的注册类型：全局注册和局部注册。  
全局注册的组件可以用在其被注册之后的任何(通过 new Vue)新创建的Vue根实例,也包括其组件树中的所有子组件的模板中.  
3.可以使用 v-bind 来动态传递 prop  
4.子组件可以通过调用内建的 $emit 方法 并传入事件名称来触发一个事件  
  
13.DOM操作  
===
重点  
this(vue).$refs  
说明:https://cn.vuejs.org/v2/api/#ref  
dom元素绑定`ref="***"`  
`this.$refs.***`  

14.过渡效果  
===
https://cn.vuejs.org/v2/guide/transitions.html  
在以下情形中可以给任何元素和组件添加进入/离开过渡  
条件渲染 (使用 v-if)  
条件展示 (使用 v-show)  
动态组件  
组件根节点  
在进入/离开的过渡中，会有 6 个 class 切换  
v-enter  
v-enter-active  
v-enter-to  
v-leave  
v-leave-active  
v-leave-to  
  
  
过滤器  
https://cn.vuejs.org/v2/guide/filters.html#ad  
                    

    
        
