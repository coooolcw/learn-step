[托管给apache的官网](https://echarts.apache.org/)  
  
需要注意的操作要点:  
1.按需引入  
```
// 引入 ECharts 主模块
var echarts = require('echarts/lib/echarts');
// 引入柱状图
require('echarts/lib/chart/bar');
// 引入提示框和标题组件
require('echarts/lib/component/tooltip');
require('echarts/lib/component/title');
```
[按需引入的列表](https://github.com/apache/incubator-echarts/blob/master/index.js)  
2.异步加载  
在图表初始化后不管任何时候只要通过 jQuery 等工具异步获取数据后通过`setOption`填入数据和配置项就行  
可先设置图标格式与样式以及显示空的图标基础样式,ajax获取数据后再填充数据  
