注意递归会有递归栈深度的限制,而循环没有.  
因此递归有时会因为递归层数过多导致游览器报错  
此时应当将递归转化为循环语句  
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/throw  

throw的用法  
---
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/try...catch  
try catch  
---
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Control_flow_and_error_handling  
MDN错误处理教程(页面下半部)  
  
注意finally 一定会被执行,优先级很高,哪怕中途使用return也无法阻止  
  
