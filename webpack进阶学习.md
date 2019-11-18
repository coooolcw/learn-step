杂记  
1.在每个vue文件的scss中自动添加变量文件,减少不必要的书写  
vue.config.js  
```
module.exports = {
  css: {
    loaderOptions: {
      // 传入公用变量
      scss: {
        prependData: `@import "~@/assets/scss/variable.scss";` //变量地址
      }
    }
  }
};
```
[官网链接](https://cli.vuejs.org/zh/guide/css.html#%E5%90%91%E9%A2%84%E5%A4%84%E7%90%86%E5%99%A8-loader-%E4%BC%A0%E9%80%92%E9%80%89%E9%A1%B9)  
