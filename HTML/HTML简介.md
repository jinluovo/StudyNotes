#### HTML简介：
1. HTML 是用来描述网页的一种语言
  * HTML 指的是超文本标记语言（Hyper Text Markup Language）
  * HTML 不是一种编程语言，而是一种标记语言
  * 标记语言是一套标记标签
  * HTML 使用标记标签来描述网页
2. HTML 标签：
  * HTML标签是由`尖括号`包围的关键词，如`<html>`
  * HTML标签通常是成对出现的，如`<b>和</b>`，其中第一个为`开始标签`（开放标签），第二个为`结束标签`（闭合标签）
3. HTML文档 = 网页
  * HTML文档描述网页
  * HTML文档包含HTML标签和纯文本
  * HTML文档也称为网页
  >Web 浏览器的作用是读取 HTML 文档，并以网页的形式显示出它们。浏览器不会显示 HTML 标签，而是使用标签来解释页面的内容

#### HTML 基础：
1. HTML标题：HTML 是通过 `<h1>-<h6>`等标签定义的，浏览器会自动在标题前后添加空行
```html
<h1>This is a heading</h1>
<h2>This is a heading</h2>
<h3>This is a heading</h3>
```
  * 标题对齐方式属性：`align`
  ```html
  <h1 align="center">******</h1>
  ```
2. HTML段落：HTML 段落是通过标签 `<p>` 标签进行定义的，浏览器会自动在段落前后添加空行
```HTML
<p>This is a paragraph.</p>
<p>This is another paragraph.</p>
```
  * 若希望在不产生新的段落的情况下换行，则使用`<br/>`标签，在显示页面时，浏览器会移除源代码中多余的空格和空行，所有连续的空格或空行都会被算作一个空格
3. HTML 链接：HTML链接是通过 `<a>` 标签定义的
```HTML
<a href="http://www.3school.com.cn">This is a link</a>
```
  * 在 href 属性中指定链接的地址

4. HTML 图像：HTML图像是通过 `<img>` 标签定义的
```HTML
<!--语法-->
<img src="图片地址" alt="下载失败时的替换文本" title = "提示文本">
<img src="w3school.jpg" width="104" height="142" />
```
  * 图片的名称和尺寸是以属性的形式提供的
  * src：标识图像的位置；
  * alt：指定图像的描述性文本，当图像不可见时（下载不成功时），可看到该属性指定的文本；
  * title：提供在图像可见时对图像的描述(鼠标滑过图片时显示的文本)；
  * 图像可以是GIF，PNG，JPEG格式的图像文件。
5. `<html>` 与 `</html>` 之间的文本描述网页，
    `<body>` 与 `</body>` 之间的文本是可见的页面内容
6. table ：定义 HTML 表格
7. HTML 换行标签：`<br/>`              
   HTML水平线：`<hr/>`                  
   HTML注释方法：`<!-- This is a comment -->`

#### HTML元素：
1. HTML 元素指的是从开始标签到结束标签的所有代码。
2. HTML元素语法：
  * 某些HTML元 素具有空内容
  * 空内容在开始标签中进行关闭（以开始标签的结束而结束）
  * 大多数HTML元素可拥有属性
  * 大多数 HTML 元素可以嵌套（可以包含其他 HTML 元素）。HTML 文档由嵌套的 HTML 元素构成。
  ```html
  <html>
  <body>
    <p>This is a paragraph.</p>
  </body>
</html>
  ```
  * 空的 HTML 元素：没有内容的 HTML 元素被称为空元素。空元素是在开始标签中关闭的。`<br>` 就是没有关闭标签的空元素（`<br>` 标签定义换行）。在开始标签中添加斜杠，比如`<br/>` 是关闭关闭空元素的正确方法
  * 规范：使用小写标签、小写属性

#### HTML 属性：
>属性为 HTML 元素提供附加信息

1. HTML 标签可以拥有属性，属性提供了 HTML 元素的更多信息，属性总是以`名称/值对`的形式出现，比如：name = "value"，属相总是在 HTML 元素的开始标签中规定
  * style ： 提供了一种改变所有 HTML 元素样式的通用方法
  ```HTML
  <!-- 定义背景颜色 -->
  <html>
  <body style="background-color:yellow">
  <h2 style="background-color:red">This is a heading</h2>
  <p style="background-color:green">This is a paragraph.</p>
  </body>
  </html>
  ```
  ```HTML
  <!-- 定义字体、颜色和尺寸 -->
  <html>
  <body>
    <h1 style="font-family:verdana">This is a heading.</h1>
    <p style="font-family:arial;color:red;font-size:20px;">A paragraph.</p>
  </body>
</html>
  ```
  ```HTML
  <!-- 定义元素的文本对齐方式 -->
  <html>
  <body>
    <h1 style="text-align:center">This is a heading.</h1>
  </body>
  </html>
  ```
  * align ：定义对齐方式
  ```html
  <h1 align="center">******</h1>
  ```
  * bgcolor ：定义背景颜色
  ```html
  <body bgcolor="yellow">******<body>
  ```
  * border ：定义表格边框相关信息
  ```HTML
  <table border="1">
  ```
2. 属性应使用小写，属性值应添加引号，一般为双引号，若属性值本身就含有双引号，则使用单引号。
```html
name='Bill "HelloWorld" Gates'
```

#### HTML 文本格式化：
* 文本格式化标签:           

![1](E:\Github\StudyNotes\Picture\文本格式化标签.png)
* 计算机输出标签：

![2](E:\Github\StudyNotes\Picture\计算机输出标签.png)
* 定义引用和术语：

![3](E:\Github\StudyNotes\Picture\定义引用和术语.png)


#### HTML CSS：
>使用添加到 `<head>` 部分的样式信息对 HTML 进行格式化。
```HTML
<html>
<head>
<style type="text/css">
h1 {color: red}
p {color: blue}
</style>
</head>
<body>
<h1>header 1</h1>
<p>A paragraph</p>
</body>
</html>
```

* `<head>` 标签用于定义文档的头部，他是所有头部元素的容器，`<head>`中的元素可以引用脚本、指示浏览器在哪里找到样式表，提供元信息等。文档的头部描述了文档的各种属性，包括文档的标题，在 web 中的位置和其他文档的关系等，绝大多数文档头部包含的数据都不会真正作为内容显示给读者。可用在 <head> 部分的标签：
  *  `<base>`标签为页面上的所有链接规定默认地址或默认目标，通常情况下，浏览器会从当前文档的 URL 中提取相应的元素来填写相应的 URL中的空白。（位于head元素内部）
  2. `<link>`标签定义文档与外部资源的关系，<link>标签最常见的用途是链接样式表。（位于head元素内部）
  3. `<meta>`标签可提供有关页面的元信息，比如针对搜索引擎和更新频度的描述和关键词，元数据总是以`名称/值`的形式被成对传递。（位于head元素内部）
  4. `<script>`标签用于定义客户端脚本，比如JavaScript，script元素既可以包含脚本语言，也可以通过 src 属性指向外部脚本文件。
  + `<style>`标签用于为HTML文档定义样式信息，type属性是必须的，定义style元素的内容，唯一可能的值是"tetx/css"。（位于head元素内部）
  + `<title>`元素定义文档的标题，是`<head>` 标签中唯一要求包含多的东西。  

#### HTML标签
+ 加入强调语气：
    * `<em>`表示强调，在浏览器中默认用<em>斜体</em> 表示
    * `<strong>`表示更强烈的强调，在浏览器中默认用<strong>粗体</strong>表示
+ `<span>`:设置单独样式
```html
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>了不起的盖茨比</title>
<style>
span{
    color:blue;
}
</style>
</head>
<body>
    <p>1922年的春天，一个想要成名名叫尼克•卡拉威（托比•马奎尔Tobey Maguire 饰）的作家，离开了美国中西部，来到了纽约。那是一个道德感渐失，爵士乐流行，走私为王，股票飞涨的时代。为了追寻他的<span>美国梦</span>，他搬入纽约附近一海湾居住。</p>
    <p>菲茨杰拉德，二十世纪美国文学巨擘之一，兼具作家和编剧双重身份。他以诗人的敏感和戏剧家的想象为"爵士乐时代"吟唱华丽挽歌，其诗人和梦想家的气质亦为那个奢靡年代的不二注解。</p>
</body>
</html>
```
+ `<q>`标签，短文本引用：双引号引用

  `<blockquote>`标签，长文本引用：缩进样式
+ `<br/>`标签用于换行，分行显示文本
+ `&nbsp;` 用于添加空格
+ `<hr/>`标签用于添加一些分割横线
+ `<address>`标签用于为网页加入地址信息
+ `<code>`标签用于在文章中插入一行代码
+ `<pre>`标签用于在文章中插入多行代码
+ `<ul>`添加没有前后顺序的信息列表
```html
<ul>
  <li>精彩少年</li>
  <li>美丽突然出现</li>
  <li>触动心灵的旋律</li>
</ul>
```
+ `<ol>`标签添加有前后顺序的信息列表
```html
<ol>
   <li>前端开发面试心法 </li>
   <li>零基础学习html</li>
   <li>JavaScript全攻略</li>
</ol>
```
+ `<div>`标签可以为网页划分独立的版块，相当于一个容器，可以用id属性给`<div>`命名，使逻辑更清晰
```html
<div id="hotList"><h2>热门课程排行榜</h2>
    <ol>
        <li>前端开发面试心法 </li>
        <li>零基础学习html</li>
        <li>javascript全攻略</li>
    </ol></div>
    <div><h2>最新课程排行</h2>
    <ol>
        <li>版本管理工具介绍—Git篇 </li>
        <li>Canvas绘图详解</li>
        <li>QQ5.0侧滑菜单</li>
    </ol></div>
```
+ `<table>`标签用于在网页上展示表格，创建表格的几个元素有：
	+ `<table>`:整个表格以`<table>`标记开始，以`</table>`标记结束
	+ `<tbody>`:如果不加`<thead>`、`<tbody>`、`<tfooter>`，表格加载完完后才显示，加上这些表格结构，tbody 包含行的内容下载完优先显示，不必等待表格结束后再显示，同时如果表格很长，用tbody分段，可以一部分一部分的显示
	+ `<tr>`：表格的一行
	+ `<td>`：表格的一个单元格
	+ `<th>`：表格头部的一个单元格，表格表头
```html
<table>
  <tbody>
    <tr>
      <th>班级</th>
      <th>学生数</th>
      <th>平均成绩</th>
    </tr>
    <tr>
      <td>一班</td>
      <td>30</td>
      <td>89</td>
    </tr>
    <tr>
      <td>二班</td>
      <td>35</td>
      <td>85</td>
    </tr>
    <tr>
        <td>三班</td>
        <td>32</td>
        <td>80</td>
    </tr>
  </tbody>
</table>
```
      + 为表格加入边框
      ```html
      <!-- 为th,td单元格添加粗细为一个像素的黑色边框 -->
      <style type="text/css">
      table tr td,th{border:1px solid #000;}
      ```
      + 为表格添加标题`<caption>`和摘要`<table summary="表格简介文本">`
      ```html
      <table summary="本表格记录2012年到2013年库存记录，记录包括U盘和耳机库存量">
      <caption>2012年到2013年库存记录</caption>
      ```
+ 使用`<a>`标签实现超链接：
```html
<!-- 语法 -->
<a  href="目标网址"  title="鼠标滑过显示的文本">链接显示的文本</a>
<!-- 默认在当前浏览器窗口中打开链接网页 -->
```
  + 在新建浏览器窗口中打开链接
  ```html
  <!-- 语法 -->
  <a href="目标网址" target="_blank">click here!</a>
  ```
  + 使用mailto在网页中链接Emali地址
  ![关键字](..\Picture\关键字.jpg)
    + 如果mailto后面同时有多个参数的话，第一个参数必须以“?”开头，后面的参数每一个都以“&”分隔。
    ![语法](..\Picture\语法.jpg)
+ 使用表单标签 `<form>` ，与用户交互：
```html
<!-- 语法 -->
<form method="传送方式" action="服务器文件">
```
      action：浏览者输入的数据被传送到的地方，比如一个PHP页面（save.php）
      method：数据传送的方式（get/post）
      所有的表单控件（文本框、文本域、按钮、单选框、复选框等）都必须放在`<form>`和`</form>`标签之间，否则用户输入的信息可能提交不到服务器上。
  + 文本输入框、密码输入框
  ```html
  <form>
  <input type="text/password" name="名称" value="文本">
  </form>
  ```
    + type:当type为text时，输入框作为文本输入框；当type为password时，输入框作为密码输入框
    + name：为文本框命名，以备后台程序ASP、PHP使用
    + value：为文本框设置默认值（一般起到提示作用）
  + 文本域标签`<textarea>`，支持多行文本输入
  ```html
  <!-- 语法 -->
  <textarea rows="行数" cols="列数">文本</textarea>
  ```
  + 单选框、复选框
  ```html
  <!--语法-->
  <input type="radio/checkbox" value="值" name="名称" checked="checked">
  ```
    + type：为radio时，控件为单选框，同一组的单选按钮，name取值应一致；为checkbox时，控件为复选框
    + value：提交数据到服务器的值（后台程序PHP使用）
    + name：为控件命名，以备后台程序ASP、PHP使用
    + checked：当设置checked为checked时，该选项被默认选中
  + 下拉列表框`<select>`，选项标签`<option>`
    + value：‘提交值’为向服务器提交的值，‘选项’为显示的值
    ```html
    <option value="提交值">选项</option>
    ```
    + selected：值为selected时，该选项就默认选中
    + 多选：在`<select>`标签中设置multiple="multiple"属性，即可实现多选功能
  + 提交按钮：只有当type值为submit时，按钮才有提交作用；value的值表示按钮上显示的文字
  ```html
  <!-- 语法 -->
  <input type="submit" value="提交">
  ```
  + 重置按钮：只有当type的值为reset时，按钮才有重置作用；value的值表示按钮上显示的文字
  ```html
  <!-- 语法 -->
  <input type="reset" value="重置">
  ```
  + form表单中的`<label>`标签，他不会向用户呈现任何特殊效果，他的作用就是为鼠标用户改进了可用性，若在label标签内点击文本，就会触发此控件，即当用户单击选中该label标签时，浏览器就会自动将焦点转到和标签相关的表单控件上（就自动选中和该label标签相关联的表单控件上）
  ```html
  <!-- 语法 -->
  <label for="控件id名">
  ```
    + 标签的for属性中的值应当与相关控件的id属性值一样
