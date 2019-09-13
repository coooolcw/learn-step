在一次数据处理中计算属性遇到了传参的问题  
由于只需要渲染一次使用methods并不合适  
但是计算属性无法直接传参,会报错不是一个函数  
查阅文档未找到能传参的说明  
  
搜索以后发现可以使用闭包来return出去一个函数,这个函数来接收参数  
HTML  
```
<li v-for="(item,index) in tabItems" :key="index" class="list-item">
        <a :href="getAnchorPoint(item.id)" @click.prevent="clickLink(item.id)">{{item.text}}</a>
</li>
```
JS  
```
computed: {
      getAnchorPoint: function() {
        return function(id) {
          return `#${id}`;
        };
      }
    }
```
这样就能在计算属性中接收参数了  
查阅资料:  
https://segmentfault.com/q/1010000009648670  
