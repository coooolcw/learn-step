babel 官网  
https://babeljs.io/  
中文网  
https://www.babeljs.cn/  
  
  
开发模式  
babel-cli  
`npm install --save-dev @babel/core @babel/cli`  
  
vue中的babel  
配置  
Vue CLI 使用了 Babel 7 中的新配置格式 babel.config.js.  
和.babelrc或package.json中的babel字段不同，这个配置文件不会使用基于文件位置的方案，  
而是会一致地运用到项目根目录以下的所有文件，包括 node_modules 内部的依赖。  
我们推荐在 Vue CLI 项目中始终使用 babel.config.js 取代其它格式。  
  
polyfill  
https://cli.vuejs.org/zh/guide/browser-compatibility.html#polyfill  
一个默认的 Vue CLI 项目会使用 @vue/babel-preset-app，它通过 @babel/preset-env 和 browserslist 配置来决定项目需要的 polyfill。  
一般设置游览器即可,不需要特别引入  
        
