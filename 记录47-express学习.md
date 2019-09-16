基础node常用模块  
1.http  
2.url  
3.util  
4.fs  
    
一般使用express框架进行开发(避免重复发明轮子)  
中文api地址(只有4.0版本,5.0的测试版没有)  
https://expressjs.com/zh-cn/  
使用时注意看一下英文文档,可能会有改动  
  
使用express-generator生成模板  
  
  
常用的模板引擎  
jade  
http://jade-lang.com/  
在线转换  
http://naltatis.github.io/jade-syntax-docs/  
  
  
MDN上的学习路径  
https://developer.mozilla.org/zh-CN/docs/Learn/Server-side/Express_Nodejs  
  
安装  
npm,node(略)  
  
npm init 创建package文件  
  
安装express  
npm install express  
  
启动服务  
node 文件名.js  
  
eslint  
`npm install eslint --save-dev`
  
设置一个配置文件：  
./node_modules/.bin/eslint --init  
记得选项使用js文件  
  
配置package.json  
```
  "scripts": {
    //添加以下
    "lint": "eslint **.js"
  }
```
之后可以npm run lint  
  
  
配置eslint选项  
```
module.exports = {
  env: {
    browser: true,
    commonjs: true,
    es6: true
  },
  extends: "eslint:recommended", //开启默认规则
  globals: {
    Atomics: "readonly",
    SharedArrayBuffer: "readonly"
  },
  parserOptions: {
    ecmaVersion: 2018
  },
  rules: {
    semi: ["error", "always"], //必须分号结尾
    "arrow-spacing": ["error", { before: true, after: true }], //箭头函数括号前后都有空格
    "space-before-function-paren": [
      "error",
      {
        anonymous: "never",
        named: "never",
        asyncArrow: "always"
      }
    ], //匿名函数命名函数括号前都没有空格,箭头函数有
    indent: ["error", 2] //与vue项目需要不同配置
  }
};
```
  
express生成器安装  
`npm install express-generator -g`  
  
在当前目录创建名为myapp的Express 应用程序(以pug,也就是jade为模板)  
`express --view=pug myapp`
  
  
文件目录结构  
```
  .
  ├── app.js
  ├── bin
  │   └── www
  ├── package.json
  ├── public
  │   ├── images
  │   ├── javascripts
  │   └── stylesheets
  │       └── style.css
  ├── routes
  │   ├── index.js
  │   └── users.js
  └── views
      ├── error.pug
      ├── index.pug
      └── layout.pug
```
app.js  入口文件  
www 执行文件  
routes文件夹存放路由文件  
public静态文件库  
views模板文件夹,格式为pug(jade)  
  
  
跨域配置中间件  
github  
https://github.com/expressjs/cors  
  
基础配置  
在router中引入cors()作为参数即可  
    
安全配置相关暂缓,本地localhost无法模拟  
放到vps上后设置origin  
只有get接口,暂时没什么必要设置源,要看就看嘛  
后期把博客后台写了再弄这个  
  
