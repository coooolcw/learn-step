https://cn.vuejs.org/v2/guide/routing.html  
重要API  
  
  router实例的基础配置  
    https://router.vuejs.org/zh/api/#routes  
  
  
route文档  
https://router.vuejs.org/zh/guide/#javascript  
HTML跳转  
```
  <!-- 使用 router-link 组件来导航. -->
  <!-- 通过传入 `to` 属性指定链接. -->
  <!-- <router-link> 默认会被渲染成一个 `<a>` 标签 -->
  <router-link to="/foo">Go to Foo</router-link>
```
  
JS跳转  
  https://router.vuejs.org/zh/guide/essentials/navigation.html  
  语法`router.push(location, onComplete?, onAbort?)`  
  在 Vue 实例内部，你可以通过 $router 访问路由实例。因此你可以调用 this.$router.push  
传参  
  基础传参  
```
    const User = {
      template: '<div>User {{ $route.params.id }}</div>'
    }
    const router = new VueRouter({
      routes: [
      { path: '/user/:id', component: User }
    ]
    })
```
  
点击 `<router-link :to="...">` 等同于调用 `router.push(...)`。  
  重要的路由对象属性  
    $route.path  
    $route.params  
    $route.query  
  重要路由实例方法  
    router.push  
  
  
☆注意在独立需要封装路由的组件中可以直接使用$router实例进行操作  
  
  
基本配置  
  在router.js中  
```
  import Home from './views/home/index.vue'
  import xxxx from './views/home/xxxx.vue'
  import about from './views/about/index.vue'
```
  普通的文件会在进入首页时就加载,懒加载的会在点击后开始加载  
```
  export default new Router({
  mode: 'history',
  base: process.env.BASE_URL,
  routes: [
    {
      //普通模式
      path: '/',
      name: 'home',
      component: Home,
      //二级路由
      children: {
        name: 'home-xxxx'
        path: 'xxxx',
        component: xxxx
      }
    },
    {
      //懒加载模式,懒加载不需要先导入,会在点击后进行加载
      path: '/about',
      name: 'about',
      // route level code-splitting
      // this generates a separate chunk (about.[hash].js) for this route
      // which is lazy-loaded when the route is visited.
      component: () => import(/* webpackChunkName: "about" */ './views/About.vue')
    },
    {
      //匹配其他所有未定义的路径
      path: '*',
      redirect: '/home',  //同path
    }
  ]
})
```
