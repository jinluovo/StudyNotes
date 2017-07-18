#### CSS样式
>CSS全称为“层叠样式表”，他主要是用于定义HTML内容在浏览器中的显示样式，如文字大小、颜色、字体加粗等。使用CSS样式可以通过定义某个样式，让不同网页位置的文字有着统一的字体、字号或颜色
```css
<style type="text/css">
p{
   font-size:20px;/*设置文字字号*/
   color:red;/*设置文字颜色*/
   font-weight:bold;/*设置字体加粗*/
}
```
```css
<!--使用CSS样式设置文本中几个短语的样式 <span>标签-->
<style type="text/css">
span{
   color:blue;
}
</style>
</head>
<body>
    <p>慕课网，<span>超酷的互联网</span>、IT技术免费学习平台，创新的网络一站式学习、实践体验；<span>服务及时贴心</span>，内容专业、<span>有趣易学</span>。专注服务互联网工程师快速成为技术高手！</p>
</body>
```

+ CSS代码语法：
  + CSS样式由选择符和声明组成，而声明又由属性和值组成

   ![CSS样式语法](..\Picture\CSS语法.jpg)
    + 选择符：又称选择器，指明网页中要应用样式规则的元素。标签选择器、类选择器
            * 标签选择器：就是HTML代码中的标签
                如 p{font-size:12px;line-height:1.6em;}
            * 类选择器：英文圆点开头，类选择器名称可以随便取，在文档中可以使用多次，而且可以使用类选择器词列表法为一个元素同时设置多个样式   
                如 .类选择器名称{css样式代码;}  <span class="类选择器名称">文本</span>
            * ID选择器：以#开头，在文档中只能使用一次  
                如 #ID选择器名称{css样式代码;}  <span id="ID选择器名称">文本</span>
            * 子选择器：即加入 >，用于选择指定标签元素的第一代子元素  
                如 .first>span{border:1px solid red;}这行代码会使类名为first下的子元素span加入红色实线边框
            * 包含（后代）选择器：即加入空格，用于指定标签元素下的所有后辈元素
                如 .first  span{color:red;}
            * 通用选择器：是功能最强大的选择器，它使用一个“ * ”指定，他的作用是匹配HTML中的所有标签元素
                如 * {color:red;}
            * 伪类选择器：“ :hover ” 它允许给HTML不存在的标签（标签的某种状态）设置样式，如鼠标滑过时的状态
                如 a:hover{color:red;} 这行代码会使标签为a的元素在鼠标滑过时颜色为红色  
            * 分组选择符：“,” 可以为HTML中的多个标签元素设置同一个样式
                如 h1,span{color:red;}  这行代码可以使标签为h1和span的元素字体为红色

    + 声明：在英文大括号"{}"中的就是声明，属性和值之间用英文冒号":"分隔，当有多条声明时，中间可以用英文分号";"分隔
  + CSS注释用`/*   */`来注释
+ CSS样式插入基本形式：
  + 内联式：将CSS代码直接写在现有的HTML标签中
  ```css
  <p style="color:red">这些文字为红色文字</p>
  ```
  + 嵌入式：把CSS样式代码写在`<style type="text/css"></style>`标签中之间，并且嵌入式CSS样式写在`<head></head>`之间
  ```css
  <style type="text/css">
span{
color:red;
}
</style>
  ```
  + 外部式：把css代码写到一个单独的外部文件中，这个css样式文件以`.css`为扩展名，在`<head>`内使用`<link>`标签将css样式文件链接到HTML文件内
  ```css
  <link href="base.css" rel="stylesheet" type="text/css" />
  ```
    + css样式文件名以有意义的英文字母命名
    + rel="stylesheet" type="text/css" 是固定写法不可修改。
    + <link>标签位置一般写在<head>标签之内。

>三种样式的优先级：内联式 > 嵌入式 > 外部式

#### css的继承、层叠、特殊性和重要性：
* css中的`某些样式`(如字体颜色、大小)是有继承性的，它允许某些样式不仅应用于某个特定的HTML标签元素，而且应用于他的后代。（注意有些样式不具有继承性，如border）
* 特殊性：当为同一个元素设置不同的css样式时，根据权值来判断使用哪种css样式，标签的权值为1，类选择器的权值为10，ID选择器的权值为100
* 层叠：HTML文件中对于同一个元素可以有多个css样式存在，当有相同权值的样式存在时，会根据css样式的前后顺序来决定，处于最后面的css样式会被应用
* 重要性：使用“!important”设置最高权值的样式
```css
p{color:red!important;}
```

#### css 格式化排版：
* 文字排版：
  * 字体、字号、颜色：
  ```css
  body{font-family:"宋体";font-size:20px;color:red;}
  ```
  + 粗体、斜体：
  ```css
  body{font-weight:bold;}/*粗体*/
  body{font-weight:italic;}/*斜体*/
  ```
  + 下划线、删除线：
  ```css
  span{text-decoration:underline;}/*下划线*/
  span{text-decoration:line-through;}/*删除线*/
  ```
+ 段落排版：
  + 缩进：
  ```css
  p{text-indent:2em;}/*2em表示文字的两倍大小*/
  ```
  + 行间距：
  ```css
  p{line-height:1.5em;}/*设置段落行间距为1.5倍*/
  ```
  + 中文字间隔、英文字母、英文单词间隔：
  ```css
  p{letter-spacing:20px;}/*中文字间隔、英文字母间隔*/
  p{word-spacing:20px;}/*英文单词间隔*/
  ```
  + 对齐：
  ```css
  p{text-align:center/left/right;}
  ```

#### css盒模型：
+ 元素分类：
  + 块级元素：
    + 在HTML中`<div>,<p>,<h1>-<h6>,<ol>,<ul>,<dl>,<table>,<address>,<blockquote>,<form>`为块级元素
    + 每个块级元素都是从新的一行开始，并且其后的元素也另起一行。
    + 元素的高度、宽度、行高以及顶和底边距都可设置。
    + 元素宽度在不设置的情况下，是他本身父容器的100%（和父元素宽度一致），除非设置一个宽度。
    + 设置`display:block`可以将元素显示为块级元素。
    ```css
    a{display:block;}
    ```
  + 内联元素：
    + 在HTML中`<a>、<span>、<br>、<i>、<em>、<strong>、<label>、<q>、<var>、<cite>、<code>`为内联元素
    + 内联元素和其他元素都在同一行上
    + 元素的高度、宽度及顶部和底部边距不可设置
    + 设置`diaplay:inline`可以将元素显示为内联元素。
    ```css
    div{dispaly:inline;}
    ```
  + 内联块状元素：
    + 内连块状元素同时具备内连元素和块状元素的特点,常用的内联块状元素有`<img>,<input>`
    + 设置`display:inline-block`可以将元素显示为内连块状元素。
    + 和其他元素都在一行上
    + 元素的高度、宽度、行高以及顶和底边距都可以设置
+ 盒子模型：
  + 边框：盒子模型的边框就是围绕着内容及补白的线，这条线可以设置他的粗细、样式、颜色
    + 样式：`border-style`有`dashed(虚线)、dotted(点线)、solid(实线)`三种样式
    + 边框颜色：`border-color`中可以设置十六进制颜色或颜色英文名
    + 边框宽度：`border-width`可使用像素设置
    + 若想为标签单独设置某一边的边框，如下：
    ```css
    div{border-bottom:1px solid red;}
    ```
  + 盒模型的宽度和高度：
    >盒模型的宽度和高度和我们平常所说的物体的宽度和高度是不一样的，css定义的宽和高，指的是填充以里的内容范围。因此，一个元素实际宽度=左边界+左边框+左填充+内容宽度+右填充+右边框+右边界

    ```css
    <!--元素实际长度为262px-->
    div{
    width:200px;
    padding:20px;
    border:1px solid red;
    margin:10px;    
}
    ```
  + 填充：元素内容与边框之间是可以设置距离的，称之为填充。填充也可以分为上、右、下、左
  ```css
  div{padding:20px 10px 15px 30px;}
  ```
  + 边界：元素与其他元素之间的距离可以使用边界(margin)来设置，边界也是可以分为上、右、下、左
  ```css
  div{margin:20px 10px 15px 30px;}
  ```
  + 简写：
    + 代码简写：若top、right、bottom、left的值相同，如
    ```css
    margin:10px 10px 10px 10px;
    ```
    可缩写为
    ```css
    margin:10px;
    ```
    若top和bottom、left和reght值相同，如
    ```css
    margin:10px 20px 10px 20px;
    ```
    可缩写为：
    ```css
    margin:10px 20px;
    ```
    若left和right值相同，如：
    ```css
    margin:10px 20px 30px 20px;
    ```
    可缩写为：
    ```css
    margin:10px 20px 30px;
    ```

    + 颜色缩写：当你设置的颜色是16进制的色彩值时，如果每两位的值相同，可以缩写一半。例如

    ```css
    p{color:#000000;}
    p{color:#000000;}
    ```
    可缩写为：
    ```css
    p{color: #000;}
    p{color: #369;}
    ```
    + 字体缩写：例如：
    ```css
    body{
    font-style:italic;
    font-variant:small-caps;
    font-weight:bold;
    font-size:12px;
    line-height:1.5em;
    font-family:"宋体",sans-serif;
}
    ```
    可缩写为：
    ```css
    body{
    font:italic  small-caps  bold  12px/1.5em  "宋体",sans-serif;
}
    ```
      + 使用这一简写方式你至少要指定 font-size 和 font-family 属性，其他的属性(如 font-weight、font-style、font-variant、line-height)如未指定将自动使用默认值。
      + 在缩写时 font-size 与 line-height 中间要加入“/”斜扛。


#### css 布局模型：
+ 流动模型(Flow)：流动模型是默认的网页布局模式，也就是说网页在默认状态下的HTML的网页元素都是根据流动模型来分布网页内容的。
  + 块状元素都会在所处的包含元素内自上而下按顺序垂直延伸分布，因为在默认状态下，块状元素的宽度都为100%。实际上，块状元素都会以行的形式占据位置。
  + 在流动模型下，内联元素都会在所处的包含元素内从左到右水平分布显示。
+ 浮动模型：浮动模型可以让两个块状元素并排显示，`float:left/right`
```css
<!--一左一右-->
div{
    width:200px;
    height:200px;
    border:2px red solid;
}
#div1{float:left;}
#div2{float:right;}
```
+ 层模型：类似PS中的图层编辑功能
  + 绝对定位(absoute):相对于其最接近的一个具有定位属性的父包含块进行绝对定位，若不存在这样的包含块，则相对与body元素，即相对于浏览器窗口
  + 相对定位(relative):相对于偏移前的位置移动
  + 固定定位(fixed)：与absolute定位类型类似，但它的相对移动的坐标是视图（屏幕内的网页窗口）本身。由于视图本身是固定的，它不会随浏览器窗口的滚动条滚动而变化，除非你在屏幕中移动浏览器窗口的屏幕位置，或改变浏览器窗口的显示大小，因此固定定位的元素会始终位于浏览器窗口内视图的某个位置，不会受文档流动影响
  + relative 和 absolute 结合使用：
    + 参照定位的元素必须是相对定位元素的前辈元素
    + 参照定位的元素必须加入position:relative
    + 定位元素加入position:absolute，便可以使用top、bottom、left、right来进行偏移定位
    ```css
    #box3{/*参照定位的元素*/
    width:200px;
    height:200px;
    position:relative;       
}
#box4{/*相对定位元素*/
    width:99%;
 	position:absolute;
	bottom:0px;
    left:0px;
}
    ```

#### 单位和值：
+ 颜色值：
  + 英文命令颜色：
  ```css
  p{color:red;}
  ```
  + RGB颜色：由R(red),G(green),B(blue)三种颜色的比例来配色，每一项的值可以是0~225之间的整数，也可以是0%~100% 之间的百分数
  ```css
  p{color:rgb(133,45,200);}
  p{color:rgb(20%,33%,25%);}
  ```
  + 十六进制颜色：这种颜色设置方法是现在比较普遍使用的方法，其原理也是RGB设置，但是其每一项的值由0~225变成了十六进制00-ff
  ```css
  p{color:#00ffff;}
  ```
+ 长度值：目前常用到的有px（像素）、em、%百分比，要注意这三个单位都是相对单位  
  + 像素（px）：像素指的是显示器上的小点（css规范中假设“90像素=1英寸”），实际情况是与浏览器会使用显示器的实际像素值有关
  + em：就是本元素给定字体的font-size值 ，如果元素的font-size为14px，那么1em=14px
    + 注意：当给font-size设置单位为em时，此时计算标准以p的父元素的fon-size 为基础
    ```html
    <p>以这个<span>例子</span>为例。</p>
    ```
    ```css
    p{font-size:14px}
span{font-size:0.8em;}/*结果 span 中的字体“例子”字体大小就为 11.2px（14 * 0.8 = 11.2px*/
    ```
  + 百分比：
  ```css
  p{font-size:12px;line-height:130%}/*设置行高（行间距）为字体的130%（12 * 1.3 = 15.6px）*/
  ```

#### css样式设置：
+ 水平居中设置：
  + 行内元素：如果被设置元素为文本、图片等行内元素时，水平居中是通过给父元素设置text-align:center来实现的
  ```HTML
  <body>
  <div class="txtCenter">我想要在父容器中水平居中显示。</div>
</body>
  ```
  ```css
  <!--css样式-->
  <style>
  .txtCenter{
    text-align:center;
  }
  </style>
  ```
  + 块状元素：
    + 定宽块状元素：即块状元素的宽度width为固定值。可以通过设置左右margin值为auto来实现居中
    ```html
    <body>
  <div>我是定宽块状元素，哈哈，我要水平居中显示。</div>
</body>
    ```
    ```css
    <style>
    <div>{border:1px solid red;
    width:200px;/定宽*/
    mrgin:20px autto;}
    </style>
    ```
    + 不定宽块状元素：即块状元素的宽度width不确定，不定宽块状元素有三种方法居中：
      + 使用table标签:利用table标签的长度自适应性---即不定义其长度也不默认父元素body的长度（table其长度根据其内文本长度决定），因此可以看做一个定宽度块元素，然后再利用定宽度块状居中的margin的方法，使其水平居中。
      ```html
      <!--为需要设置的居中的元素外面加入一个 table 标签 ( 包括 <tbody>、<tr>、<td> )。-->
      <div>
      <table><tbody>
      <tr><td>设置我所在的div容器水平居中</td></tr></tbody>
      </table>
      </div>
      ```
      ```css
      <!--为这个 table 设置“左右 margin 居中”（这个和定宽块状元素的方法一样）。-->
      <style>
      table{
        border:1px solid;
        marign:0 auto;
      }
      </style>
      ```
      + 设置display:inline，显示类型设置为行内元素，进行不定宽元素的属性设置
      + 设置position:relative和left:50%，利用相对定位的方式，将元素向左偏移50%，即达到居中的目的。
+ 垂直居中：
  + 父元素高度确定的单行文本：通过设置父元素的height和line-height高度一致来实现。line-height 与 font-size 的计算值之差，在 CSS 中成为“行间距”。分为两半，分别加到一个文本行内容的顶部和底部。
  + 父元素高度确定的多行文本：
    + 使用插入 table  (包括tbody、tr、td)标签，同时设置 vertical-align：middle。css 中有一个用于竖直居中的属性 vertical-align，在父元素设置此样式时，会对inline-block类型的子元素都有用。
    + 在 chrome、firefox 及 IE8 以上的浏览器下可以设置块级元素的 display 为 table-cell（设置为表格单元显示），激活 vertical-align 属性
  + 隐性改display类型：当为元素（不论之前是什么类型元素，display:none 除外）设置以下 2 个句之一：position:absolute或者float：left/right，元素的display显示类型就会自动变为以 display:inline-block（块状元素）的方式显示，当然就可以设置元素的 width 和 height 了，且默认宽度不占满父元素。
