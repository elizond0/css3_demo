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