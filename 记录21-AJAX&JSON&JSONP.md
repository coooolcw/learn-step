ajax内容在学习框架以后需要在服务器上实验  
  
  MDN的ajax目录  
          https://developer.mozilla.org/zh-CN/docs/Web/Guide/AJAX  
  
  MDN入门教程  
          https://developer.mozilla.org/zh-CN/docs/Web/Guide/AJAX/Getting_Started  
  
  中文教程  
https://cloud.tencent.com/developer/article/1062382  
  
http://www.runoob.com/ajax/ajax-tutorial.html  
虽然内容一般但是还是看一下这个  
  
  红皮书p571开始  
  
    
  
  
  XMLHttpRequest.open()  
  ---
  1.默认方式为GET  
  2.除url外都可不指定  
  
  XMLHttpRequest.status属性  
  ---
  1.有较多属性值   
  2.一般判断 值>=200 && 值<300 || 值 == 304   
  
  
  .setRequestHeader  
          如果你使用 POST 数据，那就需要设置请求的MIME类型。比如，在调用 send() 方法获取表单数据前要有下面这个：  
          \`httpRequest.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');\`  
    
  
// JSON  
---
in MDN  
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/JSON  
  
官网  
http://www.json.org/json-zh.html  
  
教程  
http://www.runoob.com/json/json-intro.html  
红皮书562开始  
  
  
  1.只能使用十进制,不能使用NaN和Infinity  
  2.不支持undefined  
  
  parse和eval的区别,概括结论是出于安全考虑尽量使用parse  
  http://www.cnblogs.com/lovesong/p/6036650.html  
  
  JSON.stringify()  
  parse的逆方法  
  JSON 不能存储 Date 对象。  
  JSON.stringify() 会将所有日期转换为字符串。  
  JSON 不允许包含函数，JSON.stringify() 会删除 JavaScript 对象的函数，包括 key 和 value。  
  我们可以在执行 JSON.stringify() 函数前将函数转换为字符串来避免以上问题的发生  
  不建议在 JSON 中使用函数。  
  
  jQuery的ajax方法  
  jQuery.ajax( url [, settings ] )  
  内容较多  
  
  https://www.html.cn/jqapi-1.9/jQuery.ajax/  
  主要参数:async complete dataType error success type url   
  
  跨域  
  ---
红皮书p582  
重点:JSONP p587  
基础教程:  
https://segmentfault.com/a/1190000007935557  
  
封装后的函数  
https://www.cnblogs.com/yzhihao/p/7910505.html  
  
维基的基础说明概念清楚  
https://zh.wikipedia.org/wiki/JSONP  
