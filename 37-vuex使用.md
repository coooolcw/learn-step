1.安装  
`npm install vuex --save`
或者在cli3构建的时候选择  
  
2.创建store目录/文件  
js文件:  
```
import Vue from 'vue';
import Vuex from 'vuex';

Vue.use(Vuex);

export default new Vuex.Store({
  state: {

  },
  mutations: {

  },
  actions: {

  }
});
```
  
  
然后在main.js里引入store  
```
import store from './store'//引入store
 
new Vue({
  router,
  store,
  render: h => h(App)
}).$mount("#app");
```
