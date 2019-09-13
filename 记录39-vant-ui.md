https://youzan.github.io/vant/#/zh-CN/intro  
https://github.com/youzan/vant  
  
更新及时,issues回复快  
  
  
按需引入的方式:  
使用babel-plugin-import  
配置:babel.config.js  
```
  module.exports = {
  plugins: [
    ['import', {
      libraryName: 'vant',
      libraryDirectory: 'es',
      style: true
    }, 'vant']
  ]
};
```
然后有两种方式:  
1.在main.js中引入  
```
  import { Button } from 'vant'
  Vue.use(Button)
```
2.在组件中引入(推荐)  
```
  import { Row, Col } from "vant";
  export default {
    components: {
      [Row.name]: Row,
      [Col.name]: Col,
    }
  };
```
  之后就可以使用van-col和van-row组件  
