1.document.write()方法虽然方便,但是一旦在document加载完成以后使用,会造成整个页面被覆盖  
因此很少使用  
  
一.creat
===
1.document.createElement('')
---
https://developer.mozilla.org/zh-CN/docs/Web/API/Document/createElement  
可创建游览器不支持的标签(IE6~8),具体方法https://blog.csdn.net/yuwq123/article/details/52198612  
  
2.document.createTextNode('')  
---
https://developer.mozilla.org/zh-CN/docs/Web/API/Document/createTextNode  
  
3.document.createDocumentFragment('')
---
https://developer.mozilla.org/zh-CN/docs/Web/API/Document/createDocumentFragment  
因为文档片段存在于内存中，并不在DOM树中，所以将子元素插入到文档片段时不会引起页面回流（对元素位置和几何上的计算）。  
因此，使用文档片段通常会带来更好的性能。  
常用于创建一大段的dom结构  
常用方法fragment.appendChild(xx);  
多次添加子对象,一次添加至真实dom.  
  
4.document.createComment('')
---
https://developer.mozilla.org/zh-CN/docs/Web/API/Document/createComment  
  
二.innerHTML outerHTML
===
红皮书p294~298  
1.innerHTML  
---
https://developer.mozilla.org/zh-CN/docs/Web/API/Element/innerHTML  
注意:用 innerHTML 插入文本到网页中并不罕见。但这有可能成为网站攻击的媒介，从而产生潜在的安全风险问题。  
另外还有内存占用问题,p297  
2.outerHTML
---
https://developer.mozilla.org/zh-CN/docs/Web/API/Element/outerHTML  
不常用  
  
三.innerText outerText
=== 
红皮书p301~303  
1.innerText  
---
https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/innerText  
替代  
textContent  
https://developer.mozilla.org/zh-CN/docs/Web/API/Node/textContent  
个人认为直接使用textContent更好  
  
2.outerText
---
会删除原有元素,不推荐使用  
  
四.DOM遍历  
===
基础方法 
---
红皮书p248~253  
常用的遍历属性见p251的图.  
另有childNodes[]列表可以进行遍历  
同时还有 1.hasChildNodes()用于查询元素是否含有子节点  
2.ownerDocument属性指向整个文档的文档节点  
3.Document.documentElement返回文档根元素,只读;  
HTML 文档通常包含一个子节点 <html>，可能在它前面还有个 DOCTYPE 声明。  
XML 文档通常包含多个子节点：根元素，DOCTYPE 声明，和 processing instructions。  
所以你应该使用 document.documentElement 来获取根元素, 而不是 document.firstChild。  
实际上不用document.也可以,其他元素节点的此方法也返回根元素  
  
需要注意的点:  

```
<p>
<a></a>
</p>
```
  
此处p的第一个子节点(使用firstChild)是文本节点,空格与回车形成的文本节点  
  
重要属性:nodeType nodeName tagName  
  
nodeType的属性值可以用于判断节点类型   红皮书p248有具体信息,一般常用的值是1==普通节点  
元素遍历方法  
---
红皮书p288   
指向的对象不包括文本节点和注释节点   
childElementCount;返回子节点个数(不包括文本节点和注释)  
firstElementChild;   
lastElementChild;  
previousElementSibling;  
nextElementSibling;  
children[i];子元素列表list;children同样也有length属性;基本与childNodes类似  
  
Nodelist  
---
用各种get到的(除byid以外)的结果集合  
特点:实时更新  每次访问都会重新查询   类数组  
一般尽量少访问,同时将length属性保存起来减少查询次数  
常将内容遍历后保存到数组中  
Array.prototype.slice.call(Nodelist);调用后可直接返回新数组   
  
HTMLCollection  
---
红书p257,相当于特殊化的nodelist  
重要方法: namedItem()  可根据元素id和name值查询  
https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLCollection  
犀牛书p367的介绍更具体  
此类数组可使用[数字][字符串]访问具体元素  
  
常见的返回此集合的方法,p256~258  
document.anchors等  
  
NamedNodeMap  
---
保存元素的特性节点  集合(也算一种类数组)  ,该节点的nodeValue值就是特性的值.  
红皮书p266  
主要方法:item();getNamedItem();removeNamedItem();  
一般只用在遍历元素特性上,普通情况下使用get/setAttribute();  
  
获取节点  
---
1.`ocument.getElementById();`  
p256~257  
IE7以前会将name匹配的元素也返回,现在基本不需要考虑这个.  
只有document才有此方法  
2.`ocument.getElementsByName();` 
p256~257  
只有document才有此方法  
3.`ocument.getElementsByTagName();`  
p256~257  
只有document才有此方法  
传入`*`可获得所有元素
  
需要现代游览器的方法  
4.`getElementsByClassName();`  
p289  
可在元素上调用,返回后代啧红匹配的元素;  
可传入多个class(以空格隔开);  
返回的是一个nodelist.实时更新,也会有性能问题.  
  
5.`querySelector()`  
p286~287  
接收一个css选择器(以逗号隔开的也可以)  
可在元素上调用,返回后代啧红匹配的元素;  
返回第一个匹配的元素;  
  
6.`querySelectorAll()`  
p287  
接收一个css选择器(以逗号隔开的会返回匹配两个的);  
可在元素上调用,返回后代啧红匹配的元素;  
返回一个集合  
  
注意:1.返回的是一个Nodelist的实例,相当于一个镜像,并不会实时更新,因此性能上更好  
2.按照css规则,传入的字符串空格代表的是后代元素  
  
  
操作节点  
---
1.`someNode.appendChild()`  
P251  
在目标元素的childNodes末尾添加新元素  
返回新增的节点.如果传入的节点是已经在DOM树中的,则将其移动到新的位置,旧的位置清除.  
2.`someNode.insertBefore()`  
p252  
传入被添加的节点和参照节点,若参照元素为null则与appendChild行为一样  
传入的位置位于参照节点的前方(previousSibling)  
3.`someNode.replaceChild(newNode, oldNode)`  
p252  
替换子元素,返回被替换的节点  
4.`someNode.cloneNode()`  
p252  
传入true则为深度复制,复制整个子节点树.false则只复制节点本身.  
5.`someNode.normalize()`  
p272  
在包含多个文本节点的父节点上调用,会把所有文本节点合并.nodeValue值为各个节点拼接.不常用  
6.`someNode.splitText()`  
p273  
传入数字,在传入的位置前切割(从0开始计数),切割后返回切割的后半个新的节点.  
原先的父节点会变成包含两个子文本节点.不会改变游览到的内容  
常用于提取页面的文本内容  
  
删除节点  
---
1.`someNode.removeChild()`  
返回被移除的节点  
p252  
  
2.`innerHTML('');`  
传入空可清空子节点  
