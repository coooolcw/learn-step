eslint官网  
https://eslint.org/  
中文网  
http://eslint.cn/  
具体的规则更改方式可在http://eslint.cn/docs/rules/中查找  
  
https://www.html.cn/archives/8345  
airbnb的js代码规范  
  
  
//.editorconfig  选用airbnb风格自动创建的文件  
```
  [*.{js,jsx,ts,tsx,vue}]
  indent_style = space
  indent_size = 2
  end_of_line = lf
  trim_trailing_whitespace = true
  insert_final_newline = true
  max_line_length = 100
```
修改配置在.eslintrc.js  
的rules对象内修改  
  
  
个人使用的风格  
  空格遵循大部分标准改为两个space  
```
  rules:{ 
     'semi': ["error", "always"],                       //必须分号结尾
      'arrow-spacing': ["error", { "before": true, "after": true }],   //箭头函数括号前后都有空格
      "space-before-function-paren": ["error", {
          "anonymous": "never",
          "named": "never",
          "asyncArrow": "always"
      }],                                   //匿名函数命名函数括号前都没有空格,箭头函数有
      "indent": ["off"],               //一般js文件中缩进两个空格,在vue中必须关闭否则引起冲突
      "vue/script-indent": ["error", 2, {             //vue中eslint对于script标签的缩进处理
        "baseIndent": 1,            //顶级标签下语句的缩进倍数
        "switchCase": 1,            //case/default 下语句的缩进的倍数  
        "ignores": []               //忽略的标签
      }]
  }
```
  其他暂时跟随vscode的prettier插件默认设置进行美化,不在vue中安装  
  以后有项目后再具体调整  
  
prettier  
官网  
https://prettier.io/  
配置说明(无中文版)  
https://prettier.io/docs/en/options.html  
使用时script后的内容会自动缩进到顶格,与eslint冲突  
  
冲突原因  
vutur中的    
`Format: Script Initial Indent`  
`Format: Style Initial Indent`  
需要选择为勾选(true)  
注意此选项并不在prettier中  
        
      


