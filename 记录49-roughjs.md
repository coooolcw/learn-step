官网  
https://roughjs.com/  
API  
https://github.com/pshihn/rough/wiki  
注意引入方法  
引入`../../node_modules/roughjs/bin/wrappers/rough`  
即可使用全局变量  
`一般直接import rough from "../../node_modules/roughjs/bin/wrappers/rough";`  
  
  
使用方法    
在组件内的script中    
`import rough from "../../node_modules/roughjs/bin/wrappers/rough";`  
      
在mounted中  
```
      let svg = document.getElementById('svg');
      const rc = rough.svg(svg);
      let node = rc.rectangle(10, 10, 200, 200); // x, y, width, height
      svg.appendChild(node);
      node = rc.rectangle(120, 15, 80, 80, { fill: 'red' }); //svg模式中每次添加一个图形都需要appendchild一次
      svg.appendChild(node);
```
注意api写得不是很清楚,dom都没定义  
