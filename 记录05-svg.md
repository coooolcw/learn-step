https://developer.mozilla.org/zh-CN/docs/Web/SVG  MDN的svg目录  
https://developer.mozilla.org/zh-CN/docs/Web/SVG/Tutorial 教程  
https://alili.tech/archive/pvf3acqr888/   不错的教程  
重点可以参看MDN的综合教程  
  
主要关键知识点有  

1.viewbox  
---
实际上是画布上的视窗,带有放大功能,默认为画布的大小1:1  
概念解释https://www.w3cplus.com/html5/svg-coordinate-systems.html    视窗,viewBox和preserveAspectRatio  
https://www.zhangxinxu.com/wordpress/2014/08/svg-viewport-viewbox-preserveaspectratio/  
https://www.w3cplus.com/html5/svg-transformations.html  transform详解  
https://developer.mozilla.org/zh-CN/docs/Web/SVG/Tutorial/Basic_Shapes 基本形状   
https://developer.mozilla.org/zh-CN/docs/Web/SVG/Tutorial/Texts 文本  
文本注意0,0是以基线与左侧边框交点为基准  
textLength 设置所有文字的长度  
lengthAdjust 调整字体宽度https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/lengthAdjust  
https://developer.mozilla.org/zh-CN/docs/Web/SVG/Tutorial/Fills_and_Strokes 填充与描边  
可以引入css,但是有一些区别,引入语法也不同.在上一页有描述  
https://developer.mozilla.org/zh-CN/docs/Web/SVG/Tutorial/Clipping_and_masking 剪切 设定的两个图像重合部分才会显示   
  
遮罩  
---
https://developer.mozilla.org/zh-CN/docs/Web/SVG/Tutorial/Gradients 渐变  
线性渐变  x1y1  x2y2  表示启示与结束的点(0.00~1.00)  stop-color设定颜色  
径向渐变  cx cy r 定义生效的圆形  fx fy定义色彩圆心(焦点)  
https://developer.mozilla.org/zh-CN/docs/Web/SVG/Tutorial/Other_content_in_SVG 嵌入光栅图像(png)  
  
  
svg动画  
---
https://developer.mozilla.org/zh-CN/docs/Web/SVG/SVG_animation_with_SMIL动画参考这个  新版chrome可以实现,并未删除  
svg动画set标签无法找到合适的说明,用法似乎与animate相似,但是无dur  
注意xml与css都有的属性最好设定attributeType  
to:最终值  by:δ值  values:多个值相当于关键点      有些属性可能已经删除,使用时注意查询svg2.0版本  
  
暂停恢复 svg.pauseAnimations() svg.unpauseAnimations()  

svg引入https://developer.mozilla.org/zh-CN/docs/Web/SVG/Tutorial/Getting_Started  
http://www.w3school.com.cn/svg/svg_inhtml.asp  
也可用img插入,也可直接插入html结构  
