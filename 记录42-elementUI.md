坑:  
  1.  
```
    <el-header class="header">
        <el-row class="header-row" type="flex" justify="center">
          <el-col :md="4" :lg="4" :xl="4" class="header-aside hidden-sm-and-down">123123123</el-col>
          <el-col class="header-title" :xs="24" :sm="24" :md="16" :lg="16" :xl="16">
            <span class="header-title-contents">CONTENTS</span>
          </el-col>
          <el-col :md="4" :lg="4" :xl="4" class="header-aside hidden-sm-and-down">456r456456456456</el-col>
        </el-row>
      </el-header>
```
在添加:sm="0"和:xs="0"时,整个div消失响应式失灵,最后使用import "element-ui/lib/theme-chalk/display.css";加classhidden-sm-and-down正常  
      
