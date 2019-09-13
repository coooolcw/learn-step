安装基础依赖  
`npm i --save @fortawesome/fontawesome-svg-core`  
`npm i --save @fortawesome/vue-fontawesome`  
安装三种免费字体库  
`npm i --save @fortawesome/free-solid-svg-icons`  
`npm i --save @fortawesome/free-regular-svg-icons`  
`npm i --save @fortawesome/free-brands-svg-icons`  

在main.js中导入  
```
import { FontAwesomeIcon, FontAwesomeLayers, FontAwesomeLayersText } from '@fortawesome/vue-fontawesome'
import { fas } from '@fortawesome/free-solid-svg-icons'
import { far } from '@fortawesome/free-regular-svg-icons'
import { fab } from '@fortawesome/free-brands-svg-icons'
import { library } from '@fortawesome/fontawesome-svg-core'

Vue.component('font-awesome-icon', FontAwesomeIcon)
Vue.component('font-awesome-layers', FontAwesomeLayers)//可根据需要导入
Vue.component('font-awesome-layers-text', FontAwesomeLayersText)//可根据需要导入
  
library.add(fas, far, fab)
```
