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
