整体过程  
main.js是入口文件,一般只定向到app.vue,在app.vue中导入其他组件和书写逻辑等  
最终所有的资源和文件被导出到public/index.html中发布到dist  
  
  
一些文件介绍  
postcss  
暂时不需要自行修改,自动启用的是自动补充游览器css前缀,可使用其他插件更改css  
gitignore  
上传至git时不上传的清单  
public文件夹  
https://cli.vuejs.org/zh/guide/html-and-static-assets.html#html  
相当于老版本的静态文件夹(static)+index.html  
此处的文件不会经过webpack直接打包  
  
public/index.html  
此index是最终被导入所有代码的模板,在构建过程中,资源链接会被自动注入  
meta在此书写:主要是user-scalable=no  
  
src:主要编写的区域  
assets   主要的资源文件夹  
图片,字体等  
js和css(scss/less)的公共文件也放在这里  
  
scss常用文件梳理:  
1.变量variable  
2.mixin  
3.reset  
4.icon图标css  
5.以上几个按顺序导入的index  
6.公共组件的scss文件夹  
  
components  公共页面组件文件夹  
　　　　　多个页面通用的组件  
base      基础组件(多个项目可用型)  
　　　　　banner组件,button组件,loading组件等  
views     页面级组件  
　　　　　本身就是一个页面的组件  
　　　　　子组件也放在同目录下(非通用的)  
api/ajax/jsonp  服务器通讯组件  
  
插件配置  
babel  
https://cli.vuejs.org/zh/guide/browser-compatibility.html#polyfill  
一般不需要另外配置,只需修改适配游览器版本  
fastclick  
根据介绍,2015年以后基本不需要使用  
https://github.com/ftlabs/fastclick  
安装  
`npm install fastclick --save`(安装到发布依赖)  
使用  
`import FastClick from 'fastclick'`  
`FastClick.attach(document.body);`  
  
编写区域  
需要修改/删除的文件(有自动创建信息的)  

```
public/
  index.html    //meta添加user-scalable=no
  favicon.ico
```
  
main.js  
入口文件  
用于引入全局的插件  
一些公共的样式文件，可以在这里引入  
初始的代码意义:  
render 作用类似于template  
$mount 作用类似于el:''  
  
  
  
app.vue  
根组件  
主页面的编写(游览时的首页)  
一般不在这里引入公共css  
  
router.js  
路由配置  
具体见router的总结  
  
  
  
编写  
组件(.vue)  
style中  
引入scss时如果使用@符号会报错,必须在之前加~符号才能正常引入  
如果是绝对路径则没有这个问题  
        
        
        
        

        
        
        
        
        
        
        
        
        
        
