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

* css3制作导航菜单: @/demo/nav-menu.html