# css3_demo

## 0. 简介

* CSS3是CSS2的升级版本，3只是版本号，它在CSS2.1的基础上增加了很多强大的新功能。 目前主流浏览器chrome、safari、firefox、opera、甚至360都已经支持了CSS3大部分功能了，IE10以后也开始全面支持CSS3了。

* 在编写CSS3样式时，不同的浏览器可能需要不同的前缀。它表示该CSS属性或规则尚未成为W3C标准的一部分，是浏览器的私有属性，虽然目前较新版本的浏览器都是不需要前缀的，但为了更好的向前兼容前缀还是少不了的。
1. -webkit : chrome和safari
2. -moz : firefox
3. -ms : IE
4. -o : opera

* CSS3能做什么?
1. CSS3把很多以前需要使用图片和脚本来实现的效果、甚至动画效果，只需要短短几行代码就能搞定。比如圆角，图片边框，文字阴影和盒阴影，过渡、动画等。
2. 简化了前端开发工作人员的设计过程，加快页面载入速度。
3. 功能简述,如:选择器,圆角效果,块阴影与文字阴影,色彩(HSL,CMYK,HSLA,RGBA),渐变效果,个性化字体(@Font-Face),多背景图,边框背景图,变形处理,多栏布局,媒体查询等等

## 1. 基础功能示例

### 1. 圆角效果:border-radius是向元素添加圆角边框,可以使用px,百分比,em单位,不过兼容性不够好。  

```css
/* 实心左半圆 */
div{
    height: 100px;
    width: 50px;
    border-radius: 50px 0 0 50px;
}
```

### 2. 边框阴影:box-shadow是向盒子添加阴影。支持添加一个或者多个,box-shadow:X轴偏移量 Y轴偏移量 [阴影模糊半径] [阴影扩展半径] [阴影颜色] [投影方式]

```css
/* 添加多个阴影，只需用逗号隔开即可 */
div{
    box-shadow:4px 2px 6px #f00, -4px -2px 6px #000, 0px 0px 12px 5px #33CC00 inset;
}
```

* 阴影模糊半径与阴影扩展半径的区别
1. 阴影模糊半径：此参数可选，其值只能是为正值，如果其值为0时，表示阴影不具有模糊效果，其值越大阴影的边缘就越模糊  
2. 阴影扩展半径：此参数可选，其值可以是正负值，如果值为正，则整个阴影都延展扩大，反之值为负值时，则缩小；  

* X轴偏移量和Y轴偏移量值可以设置为负数

```css
div {
    width:100px;
    height:100px;
    box-shadow:-4px 4px 6px #666;
}
```

### 3. 边框应用图片:border-image

```css
/* 与background属性比较相似 */
div{
   background:#F4FFFA;
   width:210px; height:210px; border:70px solid #ddd;
   border-image:url(borderimg.png) 70 repeat;
}
```

### 4. 颜色-RGBA/渐变色彩

```css
/* RGBA */
background-color:rgba(100,120,60,0.5);
```

* 渐变Gradient 分为线性渐变(linear)和径向渐变(radial), IE10+、Firefox19.0+、Chrome26.0+ 和 Opera12.1+
1. 线性linear-gradient(方向,起始点,结束点)
2. 径向radial-gradient(起始点,结束点),没有方向,是从中心向外扩散

```css
/* to left 表示右向左,颜色参数可以多个 */
background-image:linear-gradient(to left, red, orange,yellow,green,blue,indigo,violet);
background-image:radial-gradient(red, orange,yellow,green,blue,indigo,violet);
```

### 5. 文字与字体

* text-overflow用来设置是否使用一个省略标记（...）标示对象内文本的溢出,经常与强制文本不换行(white-space:nowrap)和溢出隐藏(overflow:hidden)配合使用

```css
text-overflow:ellipsis;
overflow:hidden;
white-space:nowrap;
```

* word-wrap可以用来设置文本行为，当前行超过指定容器的边界时是否断开转行,break-word设置在长单词或 URL地址内部进行换行，此属性不常用，用浏览器默认值即可

```css
/* 默认normal,连续文本换行,break-word表示内容将在边界内换行 */
word-wrap:break-word
```

* 嵌入字体@font-face能够加载服务器端的字体文件，让浏览器端可以显示用户电脑里没有安装的字体。

```css
@font-face {
    font-family : 'My Font';
    src : '字体文件在服务器上的相对或绝对路径';
}
p {
    font-size :12px;
    font-family : "My Font";
    /*必须项，设置@font-face中font-family同样的值*/
}
```

* 文本阴影text-shadow可以用来设置文本的阴影效果

```css
/* text-shadow: X-Offset Y-Offset blur color; */
/* X-Offset：表示阴影的水平偏移距离，其值为正值时阴影向右偏移，反之向左偏移； */
/* Y-Offset：是指阴影的垂直偏移距离，如果其值是正值时，阴影向下偏移，反之向上偏移； */
/* Blur：是指阴影的模糊程度，其值不能是负值，如果值越大，阴影越模糊，反之阴影越清晰，如果不需要阴影模糊可以将Blur值设置为0； */
Color：是指阴影的颜色，其可以使用rgba色
text-shadow: 0 1px 1px #fff
```

### 6. 背景相关

* background-origin设置元素背景图片的原始起始位置。参数:边框|内边距(default)|内容

```css
/* 背景必须是no-repeat才有效，否则会从边框开始显示。 */
background-origin ： border-box | padding-box | content-box;
```

* background-clip用来将背景图片做适当的裁剪以适应实际需要。参数:边框(default)|内边距|内容区域|不裁切

```css
background-clip ： border-box | padding-box | content-box | no-clip;
```

* background-size设置背景图片的大小，以长度值或百分比显示，还可以通过cover和contain来对图片进行伸缩

```css
background-size: auto | <长度值px> | <百分比%> | cover拉伸填充 | contain等比缩放
```

* multiple backgrounds多重背景,就是CSS2里background的属性外加origin、clip和size组成的新background的多次叠加，缩写时为用逗号隔开的每组值；用分解写法时，如果有多个背景图片，而其他属性只有一个（例如background-repeat只有一个），表明所有背景图片应用该属性值。

```css
background ： [background-color] | [background-image] | [background-position] | [background-size] | [background-repeat] | [background-attachment] | [background-clip] | [background-origin]
```

### 8. CSS3选择器-属性选择器

* 属性选择器,css3在css2的基础上扩展了通配符,类似于正则中的 ^$*
1. '^' - 开头 : target[attr^="value"]
2. '$' - 结尾 : target[attr$="value"]
3. '*' - 所有 : target[attr*="value"]

### 9. CSS3选择器-结构性伪类选择器

* :root - 指向html标签

* :not - 否定选择器

```css
/* 匹配条件:1,input;2,type属性不为submit的 */
input:not([type="submit"]){
  border:1px solid red;
}
```

* :empty - 选择没有任何内容的元素,空格也是内容

```css
p:empty {
  display: none;
}​
```

* :target - 目标选择器，用来匹配文档(页面)的url的某个标志符的目标元素
1. 触发元素的URL中的标志符通常会包含一个#号，后面带有一个标志符名称，例如a href="#brand"中的"#brand"
2. :target就是用来匹配id为“brand”的元素（id="brand"的元素）

* :first-child / :last-child - 第一个子元素 / 最后一个子元素

* :nth-child(n) / :nth-child(n) - 正数第n个 / 倒数第n个
1. 参数n是从1开始的正数,也可以是odd,even单双数
2. n可以选0,并且进行2n+1等表达式进行选择
3. n表达式<=0时,不匹配任何元素

* :first-of-type / :last-of-type / :nth-of-type(n) / :nth-last-of-type(n) - 匹配元素,用法与child类似,但不是子元素

```css
/* 匹配第一个p元素 */
p:first-of-type {
  background: orange;
}
```

* :only-child - 匹配的元素的父元素中仅有一个子元素，而且是一个唯一的子元素。

* :only-of-type - 匹配一个元素他有很多个子元素，而其中只有一种类型的子元素是唯一的

### 10. CSS3选择器-UI元素状态伪类选择器

* :enabled / :disabled - 匹配拥有 disabled和enbaled 属性的表单元素

* :checked - 匹配拥有 checked 属性的表单元素

* ::selection - 匹配拥有突出显示的文本(用鼠标选择文本时的文本)。浏览器默认情况下，用鼠标选择网页文本是以“深蓝的背景，白色的字体”显示的

* :read-only / :read-write - 匹配拥有 readonly 属性的表单元素,只读和非只读

* ::before / ::after - 主要用来给元素的前面或后面插入内容，这两个常和"content"配合使用，使用的场景最多的就是清除浮动。

```css
.clearfix::before,
.clearfix::after {
    content: ".";
    display: block;
    height: 0;
    visibility: hidden;
}
.clearfix:after {clear: both;}
.clearfix {zoom: 1;}
```

### 11. CSS3变形

* 11.1 旋转 rotate()函数通过指定的角度参数使元素相对原点进行旋转。它主要在二维空间内进行操作，设置一个角度值，用来指定旋转的幅度。如果这个值为正值，元素相对原点中心顺时针旋转；如果这个值为负值，元素相对原点中心逆时针旋转。

```css
transform: rotate(45deg);
```

* 11.2 扭曲 skew()函数能够让元素倾斜显示。它可以将一个对象以其中心位置围绕着X轴和Y轴按照一定的角度倾斜。这与rotate()函数的旋转不同，rotate()函数只是旋转，而不会改变元素的形状。skew()函数不会旋转，而只会改变元素的形状。
1. skew(x,y)使元素在水平和垂直方向同时扭曲（X轴和Y轴同时按一定的角度值进行扭曲变形）
2. skewX(x)仅使元素在水平方向扭曲变形（X轴扭曲变形）
3. skewY(y)仅使元素在垂直方向扭曲变形（Y轴扭曲变形）

```css
transform: skew(45deg);
```

* 11.3 缩放 scale()函数 让元素根据中心原点对对象进行缩放。
1. scale(X,Y)使元素水平方向和垂直方向同时缩放（X轴和Y轴同时缩放）
2. scaleX(x)元素仅水平方向缩放（X轴缩放）
3. scaleY(y)元素仅垂直方向缩放（Y轴缩放）

```css
transform: scale(1.5);
```

* 11.4 位移 translate()可以将元素向指定的方向移动，类似于position中的relative，可以把元素从原来的位置移动，而不影响在X、Y轴上的任何Web组件。
1. translate(x,y)水平方向和垂直方向同时移动（X轴和Y轴同时移动）
2. translateX(x)仅水平方向移动（X轴移动）
3. translateY(Y)仅垂直方向移动（Y轴移动）

```css
transform: translate(50px,100px);
```

* 11.5 矩阵 matrix()是一个含六个值的(a,b,c,d,e,f)变换矩阵，用来指定一个2D变换，相当于直接应用一个[a b c d e f]变换矩阵。就是基于水平方向（X轴）和垂直方向（Y轴）重新定位元素。

```css
transform: matrix(1,0,0,1,50,50);
```

* 11.6 原点 transform-origin设置中心点，默认情况之下，其中心点是居于元素X轴和Y轴的50%处。在没有重置transform-origin改变元素原点位置的情况下，CSS变形进行的旋转、位移、缩放，扭曲等操作都是以元素自己中心位置进行变形。

```css
transform-origin: left top;
```

### 12. CSS3过渡

* 12.1 transition可以通过鼠标的单击、获得焦点，被点击或对元素任何改变中触发，并平滑地以动画效果改变CSS的属性值。

1. 在默认样式中声明元素的初始状态样式；
2. 声明过渡元素最终状态样式，比如悬浮状态；
3. 在默认样式中通过添加过渡函数，添加一些不同的样式。

* 12.2 transition过渡属性是一个复合属性，主要包括以下几个子属性：

1. transition-property:指定过渡或动态模拟的CSS属性
2. transition-duration:指定完成过渡所需的时间
3. transition-timing-function:指定过渡函数
4. transition-delay:指定开始出现的延迟时间

```css
div {
  background-color:red;
  /* transition-property为all时,表示所有具备中点値并且发生变化的属性 */
  transition: background-color .5s ease .1s;
}
div:hover {
  background-color: orange;
}
```

* 12.3 transition-property用来指定过渡动画的CSS属性名称，而这个过渡属性只有具备一个中点值的属性（需要产生动画的属性）才能具备过渡效果。

* 12.4 transition-duration属性主要用来设置一个属性过渡到另一个属性所需的时间，持续时间。

* 12.5 transition-timing-function属性指的是过渡的“缓动函数”。主要用来指定浏览器的过渡速度，以及过渡期间的操作进展情况，其中要包括以下几种函数：
1. ease 由快到慢
2. linear 匀速
3. ease-in 加速,渐显
4. ease-out 减速,渐隐
5. ease-in-out 先加速再减速,渐显渐隐效果

* 12.6 transition-delay属性和transition-duration属性极其类似，不同的是transition-duration是用来设置过渡动画的持续时间，而transition-delay主要用来指定一个动画开始执行的时间，也就是说当改变元素属性值后多长时间开始执行。

* 12.7 想改变两个或者多个css属性的transition效果时，把几个transition的声明串在一起，用逗号','隔开，然后可以有各自不同的延续时间和其时间的速率变换方式。第一个时间的值为 transition-duration，第二个为transition-delay。

```css
transition: background 0.8s ease-in 0.3,color 0.6s ease-out 0.3;
```

### 13. CSS3动画

* 13.1 Keyframes被称为关键帧，其类似于Flash中的关键帧。在CSS3中其主要以“@keyframes”开头，后面紧跟着是动画名称加上一对花括号“{…}”，括号中就是一些不同时间段样式规则。

```css
/* 可以由多个百分比构成 */
/* 其中0%和100%还可以使用关键词from和to来代表 */
@keyframes changecolor{
  0% {
    margin-left: 100px;
    background:green;
  }
  40% {
    margin-left:150px;
    background:orange;
  }
  60% {
    margin-left: 75px;
    background: blue;
  }
  100% {
    margin-left: 100px;
    background: red;
  }
}
```

* 13.2 animation-name属性主要是用来调用 @keyframes 定义好的动画。需要特别注意: animation-name 调用的动画名需要和“@keyframes”定义的动画名称完全一致（区分大小写），如果不一致将不具有任何动画效果。
1. IDENT是由 @keyframes 创建的动画名
2. none为默认值，当值为 none 时，将没有任何动画效果,这可以用于覆盖任何动画。
3. 需要在 Chrome 和 Safari 上面的基础上加上-webkit-前缀，Firefox加上-moz-。

```css
/* animation-name: none | IDENT[,none|DENT]*; */
animation-name: changecolor;
```

* 13.3 animation-duration主要用来设置CSS3动画播放时间，其使用方法和transition-duration类似，是用来指定元素播放动画所持续的时间长，也就是完成从0%到100%一次动画所需时间(单位：S秒)。

```css
/* animation-duration: <time>[,<time>]* */
animation-duration: 10s;
```

* 13.4 animation-timing-function属性主要用来设置动画播放方式。主要让元素根据时间的推进来改变属性值的变换速率，动画的播放方式。

```css
/* 和transition中的transition-timing-function一样 */
animation-timing-function:ease | linear | ease-in | ease-out | ease-in-out | cubic-bezier(<number>, <number>, <number>, <number>) [, ease | linear | ease-in | ease-out | ease-in-out | cubic-bezier(<number>, <number>, <number>, <number>)]*
```

* 13.5 animation-delay属性用来定义动画开始播放的时间，用来触发动画播放的时间点。

```css
/* animation-delay:<time>[,<time>]* */
animation-delay:2s;
```

* 13.6 animation-iteration-count属性主要用来定义动画的播放次数。

1. 通常为整数，但也可以使用带有小数的数字，其默认值为1，这意味着动画将从开始到结束只播放一次。
2. 如果取值为infinite，动画将会无限次的播放。

```css
/* animation-iteration-count: infinite | <number> [, infinite | <number>]* */
animation-iteration-count:5;
```

* 13.7 animation-direction属性主要用来设置动画播放方向。

1. normal是默认值，如果设置为normal时，动画的每次循环都是向前播放；
2. alternate，动画播放在第偶数次向前播放，第奇数次向反方向播放。

```css
/* animation-direction:normal | alternate [, normal | alternate]* */
animation-direction:alternate;
```

* 13.8 animation-play-state属性主要用来控制元素动画的播放状态。

```css
/* running/paused 播放或暂停 */
animation-play-state:paused;
```

* 13.9 animation-fill-mode属性定义在动画开始之前和结束之后发生的操作。

1. none:默认值，表示动画将按预期进行和结束，在动画完成其最后一帧时，动画会反转到初始帧处
2. forwards:表示动画在结束后继续应用最后的关键帧的位置
3. backwards:会在向元素应用动画样式时迅速应用动画的初始帧
4. both:元素动画同时具有forwards和backwards效果

```css
animation-fill-mode:forwards;
```

### 14. 多栏布局

* 14.1 CSS3增加了一个多列布局模块（CSS Multi Column Layout Module），主要应用在文本的多列布局方面，这种布局在报纸和杂志上都使用了几十年了，但要在Web页面上实现这样的效果还是有相当大的难度。

```css
/* columns：<width> || <count> */
/* <width> 定义多列中每列的宽度 || <count> 定义多列中的列数 */
columns: 200px 2;
```

* 14.2 column-width在定义元素列宽的时候，既可以单独使用，也可以和多列属性中其他属性配合使用。

```css
/* column-width: auto | <length> */
/* <auto> 元素多列的列宽将由其他属性来决定，比如前面的示例就是由列数column-count来决定。 || <length> 使用固定值来设置元素列的宽度，其主要是由数值和长度单位组成，不过其值只能是正值，不能为负值。 */
column-width: auto 200px;
```

* 14.3 column-count属性主要用来给元素指定想要的列数和允许的最大列数。

```css
/* column-count：auto | <integer> */
/* <count：auto> 表示元素只有一列，其主要依靠浏览器计算自动设置。 || <integer> 用来定义元素的列数，取值为大于0的整数，负值无效。 */
column-count:4;
```

* 14.4 column-gap主要用来设置列与列之间的间距。

```css
/* column-gap: normal || <length> */
/* <normal> 默值为1em（如果字号是px，其默认值为font-size值） || <length> 此值用来设置列与列之间的距离，其可以使用px,em单位的任何整数值，但不能是负值。 */
column-count: 3;
column-gap: 2em;
```

* 14.5 column-rule主要是用来定义列与列之间的边框宽度、边框样式和边框颜色，有点类似于常用的border属性。但column-rule是不占用任何空间位置的，在列与列之间改变其宽度不会改变任何列的位置。
1. column-rule-width:主要用来定义列边框的宽度，其默认值为“medium”，column-rule-width属性接受任意浮点数，但不接收负值。但也像border-width属性一样，可以使用关键词：medium、thick和thin
2. column-rule-style:主要用来定义列边框样式，其默认值为“none”。column-rule-style属性值与border-style属值相同，包括none、hidden、dotted、dashed、solid、double、groove、ridge、inset、outset。
3. column-rule-color:主要用来定义列边框颜色，其默认值为前景色color的值，使用时相当于border-color。column-rule-color接受所有的颜色。如果不希望显示颜色，也可以将其设置为transparent(透明色)

```css
/* column-rule:<column-rule-width>|<column-rule-style>|<column-rule-color> */
column-rule: 2px dotted green;
```

* 14.6 column-span主要用来定义一个分列元素中的子元素能跨列多少。需要基中一段内容或一个标题不进行分列，也就是横跨所有列，此时column-span就可以轻松实现。

```css
/* column-span: none | all */
/* none 默认值，表示不跨越任何列。 ||  all 表示的是元素跨越所有列，并定位在列的Ｚ轴之上。 */
column-span:all;
```

### 15. css3盒子模型

#### 15.1 W3C标准盒

* 外盒尺寸计算（元素空间尺寸）
1. element空间高度＝内容高度＋内距＋边框＋外距
2. element空间宽度＝内容宽度＋内距＋边框＋外距

* 内盒尺寸计算（元素大小）
1. element高度＝内容高度＋内距＋边框（height为内容高度）
2. element宽度＝内容宽度＋内距＋边框（width为内容宽度）

#### 15.2 IE传统下盒模型（IE6以下，不包含IE6版本或”QuirksMode下IE5.5+”）--外盒尺寸计算（元素空间尺寸）

* 外盒尺寸计算（元素空间尺寸）
1. element空间高度＝内容高度＋外距（height包含了元素内容宽度、边框、内距）
2. element宽间宽度＝内容宽度＋外距（width包含了元素内容宽度、边框、内距）
* 内盒尺寸计算（元素大小）
1. element高度＝内容高度（height包含了元素内容宽度、边框、内距）
2. element宽度＝内容宽度（width包含了元素内容宽度、边框、内距）

#### 15.3 box-sizing属性，能够事先定义盒模型的尺寸解析方式 (box-sizing: content-box | border-box | inherit)

1. content-box : 默认值，其让元素维持W3C的标准盒模型，也就是说元素的宽度和高度（width/height）等于元素边框宽度（border）加上元素内距（padding）加上元素内容宽度或高度（content width/ height），也就是element width/height = border + padding + content width / height
2. border-box : 重新定义CSS2.1中盒模型组成的模式，让元素维持IE传统的盒模型（IE6以下版本和IE6-7怪异模式），也就是说元素的宽度或高度等于元素内容的宽度或高度。从上面盒模型介绍可知，这里的内容宽度或高度包含了元素的border、padding、内容的宽度或高度（此处的内容宽度或高度＝盒子的宽度或高度—边框—内距）。
3. inherit : 使元素继承父元素的盒模型模式

### 16. Flex弹性布局

* Flexbox布局常用于设计比较复杂的页面，可以轻松的实现屏幕和浏览器窗口大小发生变化时保持元素的相对位置和大小不变，同时减少了依赖于浮动布局实现元素位置的定义以及重置元素的大小。Flexbox布局功能主要具有以下几点：
1. 屏幕和浏览器窗口大小发生改变也可以灵活调整布局；
2. 可以指定伸缩项目沿着主轴或侧轴按比例分配额外空间（伸缩容器额外空间），从而调整伸缩项目的大小；
3. 可以指定伸缩项目沿着主轴或侧轴将伸缩容器额外空间，分配到伸缩项目之前、之后或之间；
4. 可以指定如何将垂直于元素布局轴的额外空间分布到该元素的周围；
5. 可以控制元素在页面上的布局方向；
6. 可以按照不同于文档对象模型（DOM）所指定排序方式对屏幕上的元素重新排序。也就是说可以在浏览器渲染中不按照文档流先后顺序重排伸缩项目顺序。

* 具体使用[Flex_learningPath](https://github.com/elizond0/Flex_learningPath)

### 17. Media Queries-媒体类型

* Media Queries是CSS3新增加的一个模块功能，通过CSS3来查询媒体，然后调用对应的样式。其实这个功能在CSS2.1中就有出现过，只不过那个时候此功能并不强大，我们最常见的就是给打印设备添加打印样式。W3C总共列出了10种媒体类型，其中Screen、All和Print为最常见的三种媒体类型：
1. All - 所有设备
2. Braille - 盲人用点字法触觉回馈设备
3. Embossed - 盲文打印机
4. Handheld - 便携设备
5. Print - 打印用纸或打印预览视图
6. Projection - 各种投影设备
7. Screen - 电脑显示器
8. Speech - 语音或音频合成器
9. Tv - 电视机类型设备
10. Tty - 使用固定密度字母栅格的媒介，比如电传打字机和终端

#### 17.1 媒体类型的引用方法也有多种，常见的有：link标签、@import和CSS3新增的@media几种：

* link方法:link标签引用样式的时候，通过link标签中的media属性来指定不同的媒体类型。

```html
<link rel="stylesheet" type="text/css" href="style.css" media="screen" />
<link rel="stylesheet" type="text/css" href="print.css" media="print" />
```

* @import方法:可以引用样式文件，同样也可以用来引用媒体类型。@import引入媒体类型主要有两种方式，一种是在样式中通过@import调用另一个样式文件；另一种方法是在head标签中的style中引入，但这种使用方法在IE6~7都不被支持

```css
@importurl(reset.css) screen;
@importurl(print.css) print;
```

* @media是CSS3中新引进的一个特性，被称为媒体查询。@media引入媒体类型和@import有点类似也具有两方式。

1.在样式文件中引用媒体类型：  

```css
@media screen {
   选择器{/*你的样式代码写在这里…*/}
}
```

2.使用@media引入媒体类型的方式是在head标签中的style中引用。  

```html
<head>
<style type="text/css">
    @media screen{
    选择器{/*你的样式代码写在这里…*/}
}
</style>
</head>
```

#### 17.2 Media Queries使用方法

* 使用Media Queries必须要使用“@media”开头，然后指定媒体类型（也可以称为设备类型），随后是指定媒体特性（也可以称之为设备特性）。媒体特性的书写方式和样式的书写方式非常相似，主要分为两个部分，第一个部分指的是媒体特性，第二部分为媒体特性所指定的值，而且这两个部分之间使用冒号分隔。

```css
/* @media 媒体类型 and （媒体特性）{你的样式} */
@media screen and (max-width:480px){
 .ads {
   display:none;
  }
}
```

* 17.2.1 最大宽度max-width指媒体类型小于或等于指定的宽度时，样式生效。最小宽度min-width指的是媒体类型大于或等于指定宽度时，样式生效。

* 17.2.2 Media Queries可以使用关键词"and"将多个媒体特性结合在一起。也就是说，一个Media Query中可以包含0到多个表达式，表达式又可以包含0到多个关键字，以及一种媒体类型。

```css
@media screen and (min-width:600px) and (max-width:900px){
  body {background-color:#f5f5f5;}
}
```

* 17.2.3 设备屏幕的输出宽度Device Width(在智能设备上，例如iPhone、iPad等)

```html
<link rel="stylesheet" media="screen and (max-device-width:480px)" href="iphone.css" />
```

* 17.2.4 not关键词-用来排除某种制定的媒体类型

```css
@media not print and (max-width: 1200px){
  /* 样式代码 */
}
```

* 17.2.5 only关键词-指定某种特定的媒体类型，可以用来排除不支持媒体查询的浏览器。其实only很多时候是用来对那些不支持Media Query但却支持Media Type的设备隐藏样式表的。其主要有：支持媒体特性的设备，正常调用样式，此时就当only不存在；表示不支持媒体特性但又支持媒体类型的设备，这样就会不读样式，因为其先会读取only而不是screen；另外不支持Media Queries的浏览器，不论是否支持only，样式都不会被采用。

```html
<linkrel="stylesheet" media="only screen and (max-device-width:240px)" href="android240.css" />
```

### 18. Responsive设计

* Responsive设计简单的称为RWD，是精心提供各种设备都能浏览网页的一种设计方法，RWD能让你的网页在不同的设备中展现不同的设计风格。RWD不是流体布局，也不是网格布局，而是一种独特的网页设计方法。

#### 18.1 响应式设计要考虑元素布局的秩序，而且还需要做到“有求必应”，那就需要满足以下三个条件：网站必须建立灵活的网格基础；引用到网站的图片必须是可伸缩的；不同的显示风格，需要在Media Queries上写不同的样式。

* 流体网格 : 是一个简单的网格系统，参考了流体设计中的网格系统，将每个网格格子使用百分比单位来控制网格大小。这种网格系统最大的好处是让网格大小随时根据屏幕尺寸大小做出相对应的比例缩放。

* 弹性图片 : 是不给图片设置固定尺寸，而是根据流体网格进行缩放，用于适应各种网格的尺寸。而实现方法是比较简单，一句代码就能搞定的事情。img {max-width:100%;} 这句代码在IE8浏览器存在一个严重的问题，图片会失踪。 因为Media Queries并不能改变图片“src”的属性值，使用background-image给元素使用背景图片，显示/隐藏父元素，给父元素使用不同的图片，然后通过Media Queries来控制这些图片显示或隐藏。

```html
<!-- 断点解决图片自适应的例子 -->
<img src="image.jpg" data-src-600px="image-600px.jpg" data-src-800px="image-800px.jpg" alt="" />
```

```css
/* 对应的CSS代码 */
@media (min-device-width:600px){
img[data-src-600px]{
  content: attr(data-src-600px,url);
  }
}
@media (min-device-width:800px){
  img[data-src-800px] {
  content:attr(data-src-800px,url);
  }
}
```

* 媒体查询 : CSS3中得到了强大的扩展。使用这个属性可以让设计根据用户终端设备适配对应的样式。这也是响应式设计中最为关键的。可以说Responsive设计离开了Medial Queries就失去了他生存的意义。简单的说媒体查询可以根据设备的尺寸，查询出适配的样式。Responsive设计最关注的就是：根据用户的使用设备的当前宽度，你的Web页面将加载一个备用的样式，实现特定的页面风格。

* 屏幕分辨率 : 简单点说就是用户显示器的分辨率，深一点说，屏幕分辨率指的是用户使用的设备浏览您的Web页面时的显示屏幕的分辨率，比如说智能手机浏览器、移动电脑浏览器、平板电脑浏览器和桌面浏览器的分辨率。Responsive设计利用Media Queries属性针对浏览器使用的分辨率来适配对应的CSS样式。因此屏幕分辨率在Responsive设计中是一个很重要的东西，因为只有知道Web页面要在哪种分辨率下显示何种效果，才能调用对应的样式。

* 主要断点 : 主要断点，在Web开发中是一个新词，但对于Responsive设计中是一个很重要的一部分。简单的描述就是，设备宽度的临界点。在Media Queries中，其中媒体特性“min-width”和“max-width”对应的属性值就是响应式设计中的断点值。使用主要断点和次要断点，创建媒体查询的条件。而每个断点会对应调用一个样式文件（或者样式代码）

#### 18.2 Responsive布局技巧

* 常用技巧
1. 使用HTML5 Doctype和相关指南；
2. 重置好你的样式（reset.css）；
3. 一个简单的有语义的核心布局；
4. 给重要的网页元素使用简单的技巧，比如导航菜单之类元素。

* 应该避免的点
1. 尽量少用无关紧要的div；
2. 不要使用内联元素（inline）；
3. 尽量少用JS或flash；
4. 丢弃没用的绝对定位和浮动样式；
5. 摒弃任何冗余结构和不使用100%设置。

* 保持HTML简单干净，而且在页面布局中的关键部分（元素）不要过分的依赖现代技巧来实现，比如说CSS3特效或者JS脚本。快速测试HTML结构简单干净的方法，首先禁掉页面中所有的样式（以及与样式相关的信息），在浏览器中打开，如果内容排列有序，方便阅读，那么结构不会差到哪里去。

#### 18.3 meta标签

* meta标签内的content属性值:
1. width : 可视区域的宽度，值可以是一个具体数字或关键词device-width
2. height : 可视区域的高度，值可以是一个具体数字或关键词device-height
3. initial : 页面首次被显示时可视区域的缩放级别，取值为1.0时将使页面按实际尺寸显示，无任何缩放
4. minimun-scale : 可视区域的最小缩放级别，表示用户可以将页面缩小的程度，取值为1.0时将禁止缩小至实际尺寸以下
5. maximun-scale : 可视区域的最大缩放级别，表示用户可以将页面放大的程度，取值为1.0时将禁止放大至实际尺寸以上
6. user-scalable : 指定用户是否可以对页面进行缩放，设置为yes将允许缩放，no为禁止

```html
<meta name=”viewport” content=”” />
```

* 在实际项目中，为了让Responsive设计在智能设备中能显示正常，也就是浏览Web页面适应屏幕的大小，显示在屏幕上，可以通过这个可视区域的meta标签进行重置，告诉使用设备的宽度为视图的宽度，也就是说禁止其默认的自适应页面的效果。

```html
<meta name=”viewport” content=”width=device-width,initial-scale=1.0” />
```

* 由于Responsive设计是结合CSS3的Media Queries属性，才能尽显Responsive设计风格，但在IE6-8中完全是不支持CSS3 Media，可以使用html中条件注释的语法或者respond.js适应需求。

```html
<script src='respond.js'></script>
<!--[if lt IE10]>
<link rel="stylesheet" type="text/css" href="ie10-and-down.css">
<![endif]-->
```

#### 18.4 不同设备的分辨率设置

* Pad横屏

```css
@media screen and (max-device-width: 1024px) and (orientation: landscape) {
  /* 样式 */
}
```

* Pad竖屏

```css
@media screen and (max-device-width: 768px) and (orientation: portrait) {
  /* 样式 */
}
```

* iPhone 和 Smartphones

```css
@media screen and (min-device-width: 320px) and (min-device-width: 480px) {
  /* 样式 */
}  
```

### 19. 自由缩放属性resize

* 兼容性：Chrome 4；Firefox 4；Safari 4；Opera 15；Android Chrome 66；IOS Safari不兼容；IE不兼容；

* resize允许用户通过拖动的方式来修改元素的尺寸来改变元素的大小，其主要目的是增强用户体验，部分标签需要overflow属性进行配合。resize: none | both | horizontal | vertical | inherit
1. none : 用户不能拖动元素修改尺寸大小。
2. both : 用户可以拖动元素，同时修改元素的宽度和高度。
3. horizontal : 用户可以拖动元素，仅可以修改元素的宽度，但不能修改元素的高度。
4. vertical : 用户可以拖动元素，仅可以修改元素的高度，但不能修改元素的宽度。
5. inherit : 继承父元素的resize属性值。

```css
div {
  -webkit-resize: horizontal;
  -moz-resize: horizontal;
  -o-resize: horizontal;
  -ms-resize: horizontal;
  resize: horizontal;
  overflow:hidden;
}
```

### 20. 外轮廓属性outline

* 外轮廓outline在页面中呈现的效果和边框border呈现的效果和语法极其相似，但和元素边框border完全不同，外轮廓线不占用网页布局空间，不一定是矩形，外轮廓是属于一种动态样式，只有元素获取到焦点或者被激活时呈现。outline: ［outline-color］ || [outline-style] || [outline-width] || [outline-offset] || inherit
1. outline-color : 定义轮廓线的颜色，属性值为CSS中定义的颜色值。在实际应用中，可以将此参数省略，省略时此参数的默认值为黑色。
2. outline-style : 定义轮廓线的样式，属性为CSS中定义线的样式。在实际应用中，可以将此参数省略，省略时此参数的默认值为none，省略后不对该轮廓线进行任何绘制。
3. outline-width : 定义轮廓线的宽度，属性值可以为一个宽度值。在实际应用中，可以将此参数省略，省略时此参数的默认值为medium，表示绘制中等宽度的轮廓线。
4. outline-offset : 定义轮廓边框的偏移位置的数值，此值可以取负数值。当此参数的值为正数值，表示轮廓边框向外偏离多少个像素；当此参数的值为负数值，表示轮廓边框向内偏移多少个像素。
5. inherit : 元素继承父元素的outline效果。

```css
div {
  outline:#00FF00 dotted thick;
}
```

### 21. 生成内容content

* 通过CSS3的伪类“:before”，“:after”和CSS3的伪元素“::before”、“::after”来实现，其关键是依靠CSS3中的“content”属性来实现插入内容，不过这个属性对于img和input元素不起作用。
1. none : 不生成任何内容
2. string : 插入字符串
3. attr : 插入标签属性值
4. url : 使用指定的绝对或相对地址插入一个外部资源（图像，声频，视频或浏览器支持的其他任何资源）

```css
a:after{
  content: " (" attr(href) ")"
}
```

```html
<a href="http://www.w3school.com.cn">W3School</a> contains free tutorials and references.</p>
```

### 22. CSSdemo

* 1-2D旋转导航菜单: @/demo/1-transition-nav-menu.html

* 2-3d翻转导航菜单 @/demo/2-3D-rotate-nav.html

* 3-3d旋转展示区域 @/demo/3-3D-rotate-display-area.html

* 4-利用边框radius制作图标 @/demo/4-borderRadius-icon.html

* 5-多层边框box-shadow @/demo/5-multiple-border.html

* 6-径向渐变实现内凹圆角 @/demo/6-indent-radius.html