官网  
https://sass-lang.com/  

中文网  
https://www.sass.hk/docs/  
  
简单教程  
http://www.ruanyifeng.com/blog/2012/06/sass.html  
https://www.cnblogs.com/morong/p/4329957.html  
  
重点:  
  
1.变量  
===
sass的变量名必须是一个$符号开头，后面紧跟变量名  
`$red: #f00;`  
特殊变量：如果变量嵌套在字符串中，则需要写在 #{} 符号里面  
```
$top: top;
div {
    margin-#{$top}: 10px;       /* margin-top: 10px; */
}
```
默认变量：仅需在值后面加入 !default即可， 默认变量一般用来设置默认值，当该变量出现另外一个值时，  
无论定义先后，都会使用另外一个值，覆盖默认值  
```
$color: red;
$color: blue !default;
div {
    color: $color;    /* color:red; */
}
```
变量支持块级作用域，嵌套规则内定义的变量只能在嵌套规则内使用（局部变量），  
不在嵌套规则内定义的变量则可在任何地方使用（全局变量）。  
将局部变量转换为全局变量可以添加 !global 声明  
  
2.@import 
===
通常，@import 寻找 Sass 文件并将其导入，但在以下情况下，@import 仅作为普通的 CSS 语句，不会导入任何 Sass 文件。  
文件拓展名是 .css；  
文件名以 http:// 开头；   
文件名是 url()；  
@import 包含 media queries。  
如果不在上述情况内，文件的拓展名是 .scss 或 .sass，则导入成功。  
没有指定拓展名，Sass 将会试着寻找文件名相同，拓展名为 .scss 或 .sass 的文件并将其导入。  
  
如果需要导入 SCSS 或者 Sass 文件，但又不希望将其编译为 CSS，只需要在文件名前添加下划线，  
这样会告诉 Sass 不要编译这些文件，但导入语句中却不需要添加下划线。  
  
注意:import引入时也会改变变量,使用!default设置可避免位置引发的冲突  
  
3.数据类型  
===
SassScript 支持 6 种主要的数据类型：  
数字，1, 2, 13, 10px  
字符串，有引号字符串与无引号字符串，"foo", 'bar', baz  
颜色，blue, #04a3f9, rgba(255,0,0,0.5)  
布尔型，true, false  
空值，null  
数组 (list)，用空格或逗号作分隔符，1.5em 1em 0 2em, Helvetica, Arial, sans-serif  
maps, 相当于 JavaScript 的 object，(key1: value1, key2: value2)  
  
字符串  
---
SassScript 支持 CSS 的两种字符串类型：有引号字符串 (quoted strings)，如 "Lucida Grande" 'http://sass-lang.com'；  
与无引号字符串 (unquoted strings)，如 sans-serif bold，在编译 CSS 文件时不会改变其类型。  
只有一种情况例外，使用 #{} (interpolation) 时，有引号字符串将被编译为无引号字符串，这样便于在 mixin 中引用选择器名：  
  
数组  
---
数组 (lists) 指 Sass 如何处理 CSS 中 margin: 10px 15px 0 0 或者  
font-face: Helvetica, Arial, sans-serif 这样通过空格或者逗号分隔的一系列的值。  
事实上，独立的值也被视为数组 —— 只包含一个值的数组。  
  
数组本身没有太多功能，但 Sass list functions 赋予了数组更多新功能：  
nth 函数可以直接访问数组中的某一项；  
join 函数可以将多个数组连接在一起；  
append 函数可以在数组中添加新值；  
而 @each 指令能够遍历数组中的每一项。  
  
  
数组中可以包含子数组，比如 1px 2px, 5px 6px 是包含 1px 2px 与 5px 6px 两个数组的数组。  
如果内外两层数组使用相同的分隔方式，需要用圆括号包裹内层，  
所以也可以写成 (1px 2px) (5px 6px)。变化是，之前的 1px 2px, 5px 6px 使用逗号分割了两个子数组 (comma-separated)，  
而 (1px 2px) (5px 6px) 则使用空格分割(space-separated)。  
  
当数组被编译为 CSS 时，Sass 不会添加任何圆括号（CSS 中没有这种写法），  
所以 (1px 2px) (5px 6px) 与 1px 2px, 5px 6px 在编译后的 CSS 文件中是完全一样的，  
但是它们在 Sass 文件中却有不同的意义，前者是包含两个数组的数组，而后者是包含四个值的数组。  
  
用 () 表示不包含任何值的空数组（在 Sass 3.3 版之后也视为空的 map）。  
空数组不可以直接编译成 CSS，比如编译 font-family: () Sass 将会报错。  
如果数组中包含空数组或空值，编译时将被清除，比如 1px 2px () 3px 或 1px 2px null 3px。  
  
基于逗号分隔的数组允许保留结尾的逗号，这样做的意义是强调数组的结构关系，  
尤其是需要声明只包含单个值的数组时。例如 (1,) 表示只包含 1 的数组，  
而 (1 2 3,) 表示包含 1 2 3 这个以空格分隔的数组的数组。  
  
  
数组的使用方法:  
https://sass-lang.com/documentation/functions/list(英文)  
  
map
---
Maps可视为键值对的集合，键被用于定位值 在css种没有对应的概念。  

使用map  
https://sass-lang.com/documentation/values/maps  

map-get
---
Maps are all about associating keys and values,   
so naturally there’s a way to get the value associated with a key: the map-get($map, $key) function!  
This function returns the value in the map associated with the given key.  
It returns null if the map doesn’t contain the key.  
例子  
```
$font-weights: ("regular": 400, "medium": 500, "bold": 700);
@debug map-get($font-weights, "medium"); // 500
@debug map-get($font-weights, "extra-bold"); // null
```
  
@each  
---
This doesn’t actually use a function, but it’s still one of the most common ways to use maps.   
The @each rule evaluates a block of styles for each key/value pair in a map.   
The key and the value are assigned to variables so they can easily be accessed in the block.  
例子  

`$icons: ("eye": "\f112", "start": "\f12e", "stop": "\f12f");`
  
```
@each $name, $glyph in $icons {
  .icon-#{$name}:before {
    display: inline-block;
    font-family: "Icon Font";
    content: $glyph;
  }
}
```
  
3.运算  
===
除法  
以下三种情况 / 将被视为除法运算符号：   
如果值，或值的一部分，是变量或者函数的返回值  
如果值被圆括号包裹  
如果值是算数表达式的一部分  
  
例子  
```
p {
  font: 10px/8px;             // Plain CSS, no division
  $width: 1000px;
  width: $width/2;            // Uses a variable, does division
  width: round(1.5)/2;        // Uses a function, does division
  height: (500px/2);          // Uses parentheses, does division
  margin-left: 5px + 8px/2px; // Uses +, does division
}
```
编译为  
```
p {
  font: 10px/8px;
  width: 500px;
  height: 250px;
  margin-left: 9px; }
```
颜色值的运算是分段计算进行的，也就是分别计算红色，绿色，以及蓝色的值  
使用 color functions 比计算颜色值更方便一些。  
https://sass-lang.com/documentation/functions/color  
常用  mix()  red()  green()  blue() 等,详见网页  
  
4.mixin
===
定义  
混合指令的用法是在 @mixin 后添加名称与样式  
混合也需要包含选择器和属性，甚至可以用 & 引用父选择器  
```
@mixin clearfix {
  display: inline-block;
  &:after {
    content: ".";
    //...省略
  }
  * html & { height: 1px }
}
```
  
使用  
@include 指令引用混合样式，格式是在其后添加混合名称，以及需要的参数（可选）  
  
混合样式中也可以包含其他混合样式  
```
@mixin compound {
  @include highlighted-background;
  @include header-text;
}
@mixin highlighted-background { background-color: #fc0; }
@mixin header-text { font-size: 20px; }
```
混合样式中应该只定义后代选择器，这样可以安全的导入到文件的任何位置。  
原因:不会自动覆盖同级别的属性.会按照引入顺序输出  
  
参数  
参数用于给混合指令中的样式设定变量，并且赋值使用。  
在定义混合指令的时候，按照变量的格式，通过逗号分隔，将参数写进圆括号里。  
引用指令时，按照参数的顺序，再将所赋的值对应写进括号  
```
@mixin sexy-border($color, $width) {
  border: {
    color: $color;
    width: $width;
    style: dashed;
  }
}
p { @include sexy-border(blue, 1in); }
```
有时，不能确定混合指令需要使用多少个参数。  
这时，可以使用参数变量 … 声明（写在参数的最后方）告诉 Sass 将这些参数视为值列表处理  
```
@mixin box-shadow($shadows...)  {
//something
}
```
  
5.继承和嵌套  
===
继承
---
@extend  
```
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.seriousError {
  @extend .error;
  border-width: 3px;
}
```
上面代码的意思是将 .error 下的所有样式继承给 .seriousError  
  
注意:继承的是整个css树结构.相同的子结构也会继承属性  
解释:@extend 的作用是将重复使用的样式延伸 (extend) 给需要包含这个样式的特殊样式  
```
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.error.intrusion {
  background-image: url("/image/hacked.png");
}
.seriousError {
  @extend .error;
  border-width: 3px;
}
```
输出  
```
.error, .seriousError {
  border: 1px #f00;
  background-color: #fdd; }
.error.intrusion, .seriousError.intrusion {
  background-image: url("/image/hacked.png"); }
.seriousError {
  border-width: 3px; }
```
链式继承  
可嵌套进行继承  
  
伪类继承  
Class 选择器并不是唯一可以被延伸 (extend) 的，  
Sass 允许延伸任何定义给单个元素的选择器，比如 `.special.cool，a:hover` 或者 `a.user[href^="http://"]` 等  
例子  
```
.hoverlink {
  @extend a:hover;
}
a:hover {
  text-decoration: underline;
}
```
输出  
```
a:hover, .hoverlink {
text-decoration: underline; }
```
所有 a:hover 的样式将继承给 .hoverlink，包括其他使用到 a:hover 的样式  
```
.hoverlink {
  @extend a:hover;
}
.comment a.user:hover {
  font-weight: bold;
}
```
编译为  
```
.comment a.user:hover, .comment .user.hoverlink {
font-weight: bold; }
```
  
嵌套
---
规则:  
1.内层的样式将它外层的选择器作为父选择器  
2.用 & 代表嵌套规则外层的父选择器  
```
a {
  font-weight: bold;
  text-decoration: none;
  &:hover { text-decoration: underline; }
  body.firefox & { font-weight: normal; }
}
```
输出  
```
a {
  font-weight: bold;
  text-decoration: none; }
a:hover {
  text-decoration: underline; }
body.firefox a {
  font-weight: normal; }
```
3.Sass 允许将属性嵌套在命名空间中,命名空间也可以包含自己的属性值  
```
.funky {
  font: 20px/24px {
    family: fantasy;
    weight: bold;
  }
}
```
输出  
```
.funky {
  font: 20px/24px;
  font-family: fantasy;
  font-weight: bold; }
```
6.条件/控制语句  
1.if  
当 @if 的表达式返回值不是 false 或者 null 时，条件成立，输出 {} 内的代码  
@if 声明后面可以跟多个 @else if 声明，或者一个 @else 声明。  
如果 @if 声明失败，Sass 将逐条执行 @else if 声明，如果全部失败，最后执行 @else 声明  
2.for  
@for 指令可以在限制的范围内重复输出格式，每次按要求（变量的值）对输出结果做出变动。  
这个指令包含两种格式：@for $var from <start> through <end>，  
或者 @for $var from <start> to <end>，区别在于 through 与 to 的含义：  
当使用 through 时，条件范围包含 <start> 与 <end> 的值，而使用 to 时条件范围只包含 <start> 的值不包含 <end> 的值。  
另外，$var 可以是任何变量，比如 $i；<start> 和 <end> 必须是整数值。  
  
  
注意:可遍历数组 不过感觉上用each更好  
```
$list:(,,,,,);//something
for $listitem from $list though length($list) {
  $listitem {
    //something
  }
}
```
3.while  
@while 指令重复输出格式直到表达式返回结果为 false。这样可以实现比 @for 更复杂的循环，只是很少会用到  
记得在循环内操作$i  
```
$i: 6;
@while $i > 0 {
  .item-#{$i} { width: 2em * $i; }
  $i: $i - 2;
}
```
4.each  
对list  
@each 指令的格式是 $var in <list>, $var 可以是任何变量名，  
比如 $length 或者 $name，而 <list> 是一连串的值，也就是值列表。  
@each 将变量 $var 作用于值列表中的每一个项目，然后输出结果  
语法:@each $size in $sizes  
对map  
https://sass-lang.com/documentation/at-rules/control/each  
语法:@each <variable>, <variable> in <expression> { ... }  
例子  
```
$icons: ("eye": "\f112", "start": "\f12e", "stop": "\f12f");
@each $name, $glyph in $icons{
  .icon-#{$name}:before {
    display: inline-block;
    font-family: "Icon Font";
    content: $glyph;
  }
}
```
7.函数  
函数列表(总)  
https://sass-lang.com/documentation/functions  
  
1.数字  
number函数列表  
https://sass-lang.com/documentation/functions/math  
重点函数  
1.random($limit: null)  
如果$limit是1,输出0\~1之间的随机数  
如果$limit是1以上的整数,输出1\~$limiti之间的随机整数  
常见函数  
```
1.abs($number) //=> number 
2.ceil($number) //=> number 
3.floor($number) //=> number 
4.max($number...) //=> number 
5.min($number...) //=> number
6.percentage($number) //=> number 
7.round($number) //=> number 
```
  
2.数组  
https://sass-lang.com/documentation/functions/list  
常见函数  
```
1.length($list) //=> number 
2.nth($list, $n) 
3.set-nth($list, $n, $value) //=> list 
4.join($list1, $list2, $separator: auto, $bracketed: auto) //=> list 
  用于合并两个数组
5.append($list, $val, $separator: auto) //=> list 
  在数组的最后添加新的值
5.index($list, $value) //=> number | null 
```
3.字符串  
https://sass-lang.com/documentation/functions/string  
常见函数  
```
1.quote($string) //=> string 
2.str-index($string, $substring) //=> number 
3.str-insert($string, $insert, $index) //=> string 
  插入字符.
4.str-length($string) //=> number 
5.to-upper-case($string) //=> string 
  to-lower-case($string) //=> string
```
4.map函数  
https://sass-lang.com/documentation/functions/map  
常见函数  
```
1.map-get($map, $key) 
2.map-remove($map, $keys...) //=> map 
3.map-keys($map) //=> list 
4.map-values($map) //=> list 
5.map-has-key($map, $key) //=> boolean 
6.keywords($args) //=> map 
```
重点  
用于mixin  
```
@mixin syntax-colors($args...) {
  @debug keywords($args); // (string: #080, comment: #800, $variable: $60b)

@each $name, $color in keywords($args) {
  pre span.stx-#{$name} {
    color: $color;
    }
  }
}

@include syntax-colors(
  $string: #080,
  $comment: #800,
  $variable: #60b,
)
```
5.自定义函数  
https://sass-lang.com/documentation/at-rules/function  
Sass 支持自定义函数，并能在任何属性值或 Sass script 中使用  
  
例子  
```
@function pow($base, $exponent) {
  $result: 1;
  @for $_ from 1 through $exponent {
    $result: $result * $base;
  }
  @return $result;
}

.sidebar {
  float: left;
  margin-left: pow(4, 3) * 1px;
}
```


