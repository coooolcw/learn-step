情形:  
  中文webfont发展水平比英文低,原因主要是中文字体文件较大,google fonts使用不稳定等  
  
    
解决方案:  
  webfont  
  1.阿里webfont平台  
    优点:阿里的cdn效果应该较好  
    缺点:需要反复手动更新无api,无法在web内使用  
    地址https://www.iconfont.cn/webfont?spm=a313x.7781069.1998910419.12&puhui=1#!/webfont/index  
  2.第三方api自动缩减体积然后通过第三方的cdn推送到客户端  
    优点:字体自动优化,动态更新  
    缺点:收费,而且第三方的cdn不能保证稳定  
    主要有两家:  
      1.https://www.webfont.com/   有字库  
      2.http://cn.justfont.com/    就是字  
  3.直接googlefonts  
    优点:来源稳定  
    缺点:哪天炸了谁都不知道  
  4.googlefonts的国内cdn  
    优点:国内网络友好  
    缺点:哪天崩了谁都不知道,搭配webfontloader使用比较合适  
    360cdn炸了以后有https://cdn.baomitu.com/    无中文字体cdn  
    另外独立的有https://cdn.geekzu.org/cached.html   字体齐全  
  5.中科院反向代理  
    https://lug.ustc.edu.cn/wiki/lug/services/revproxy  
    具体与极客族哪个好待尝试  
    
      

      
    
    
    
辅助插件  
  1.webfontloader  
    可与不同cdn搭配使用  
    
    地址https://github.com/typekit/webfontloader  
  2.字蛛  
    缩减字体体积,去除未使用的文字  
    缺陷:无法在webpack中使用,只能在gulp和grunt中使用,  
    如果在vue中使用,只能先把web导出为静态页面然后使用处理后的字体文件  
    地址:http://font-spider.org/index.html  
    
  
其他  
  1.font-display  
    https://developer.mozilla.org/zh-CN/docs/Web/CSS/@font-face/font-display  
    在@font-face中定义,可统一各游览器,但有兼容性问题  
  
  2.fontfaceobserver  
    https://github.com/bramstein/fontfaceobserver  
    类似于1的方案,可以解决兼容性问题  
    但是需要耦合js  


  

实际尝试以后,直接@import  googlefonts可以正常使用  
webfonts的管理方式总是会有几个字无法获取到字体文件,mouted和created都试过,可能和vue有所不兼容,  
会和微软雅黑混杂显示  

先用一段时间的谷歌字体,如果发现有不稳定情况再更换反向代理的@import  
