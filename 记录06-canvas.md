MDN教程  
https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial  
默认大小300*150  
注意css设置宽高与html结构直接设置(js内设置)的效果不同,CSS中设置不会改变canvas内的坐标系,仍然为默认值,会将canvas内容缩放  
可同时设置,先按照canvas设置绘制,再缩放  
  
常用语法  
---
https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes  
色彩与填充  
https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors  
  
基础变形  
---
https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Transformations  
save()restore()要常用,保存的数据较多,参看web  
translate(x, y)移动 canvas 和它的原点.同时移动,因此在不同步骤平移会有不同效果  
注意坐标系会被改变  
rotate(angle)也是转动坐标系,顺时针为正  
scale(x, y)缩放同样也是对坐标系生效  
而坐标系变化以后可以叠加,继续改变.但是坐标系改变不会影响到之前画的  
  
渐变https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors  
页面的下半段  
渐变的起点和终点是按照整个坐标系的,并不是独立的新坐标系  
  

文本  
---
https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Drawing_text  
  
使用image  
---
https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Using_images  
图案样式(使用图片填充),在页面下半部  
https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors  
  
裁切,在页面下半部  
https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Compositing  
阴影,在页面最底下  
https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors  
曲线路径,在页面下部  
https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes  
贝塞尔曲线辅助工具http://www.nicetool.net/app/canvas_bezier_code.html  
  
  
基本动画  
https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Basic_animations  
  
性能优化,canvas离屏技术  
https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Optimizing_canvas  
