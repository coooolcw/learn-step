flex布局  
===
MDN教程  
https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_flexbox_to_lay_out_web_applications  
基础概念  
https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes(这篇比较好)  
属性列表  
https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout  
  
比较好的教程  
http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html  
https://www.w3cplus.com/css3/a-guide-to-flexbox-new.html  
  
flex-wrap实质上定义了侧轴的方向.  
justify-content生效的条件是所有元素都不能拉伸或已经拉伸到了最大值  
现在阶段justify-content支持较好的几个属性是flex-start,flex-end,center,space-between,space-around  
默认值flex-start  
已经有一批新属性退出,支持尚未跟上,但是似乎非常好用,英文圈有大量讨论  
align-content  
flex-start,flex-end,center,space-between,space-around,stretch  
默认值stretch  
  
flex-grow、flex-shrink、flex-basis的理解  
http://zhoon.github.io/css3/2014/08/23/flex.html  
flex-basis新属性值content相当于设置为auto的同时设置元素的width.  
在兼容性不佳时可这样操作  
flex的简写对于属性会有不同的默认值优化,例如简写1  实际是1 1 0.因此推荐使用flex的简写.  
具体机制https://developer.mozilla.org/zh-CN/docs/Web/CSS/flex  
  
  
@media媒体查询用于响应式布局  
===
综述  
https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Media_queries  
MDN的介绍  
https://developer.mozilla.org/zh-CN/docs/Web/CSS/@media  
  
  
在使用图片时,对于img和background-image的性能对比  
https://www.jiawin.com/background-img-compare  
