### JQuery基础：
1. jQuery概述：
>jQuery是一个javascript的库（或是javascript框架），他兼容CSS3，还兼容各种浏览器，核心理念是"write less,do more"

  + 引入和对象获取：下载对应的js库下载，导入到项目下面，在HTML页面中使用`<script>`导入即可
  + 基本语法：`jQuery(选择器)`或`$(选择器)`，即在jQuery中`jQuery == $ `（区分大小写）
  ```javascript
  var $demoId = $("#demoId");
  ```
2. jQuery 对象和 DOM 的转换：
  + jQuery对象和DOM对象可以项目转换，但两个对象的函数不能彼此混搭使用，即jQuery对象只能使用自己的函数
  ```javascript
  // 1.DOM对象转换成jQuery对象，语法：
  jQuery(dom对象)
  var spanEle = document.getElementById("span1");
	//将DOM对象转换成jQ对象
	$(spanEle).html("思密达~~");
  // **************************************//
  // 2.jQuery对象转换成DOM对象，语法：
  $username[index]
  //jQ对象向DOM对象转换方式一
  $("#span1").get(0).innerHTML = "美美哒~~";
  //jQ对象向DOM对象转化方式二
  $("#span1")[0].innerHTML = "棒棒哒~~";
  ```

3. 选择器：
  + 基本选择器：
  ```
  :first--第一个
  :last--最后一个
  :even--偶数行
  :odd--奇数行
  ```
  + 层级选择器：
  ```
  a b--空格，代表其下所有的子集（儿子，孙子，曾孙）
  a>b--大于号，代表儿子
  a+b--加号，代表所有与a元素相接的b元素
  a~b--‘~’，代表a元素后的所有b元素，兄弟节点
  ```
  + 内容选择器：
  ```
  :contains--匹配包含给定文本的元素
  :empty--匹配所有不包含子元素或者文本的空元素
  :has--匹配含有选择器所匹配的元素的元素
  :parent--匹配含有子元素或者文本的元素
  ```
  + 属性选择器：
  ```
  [attritube]
  [attritube=value]
  [attritube!=value]
  ```
  + 可见性:
  ```
  :hidden
  :visible
  ```
  + 表单：
  ```
  :input：匹配所有 input, textarea, select 和 button 元素
  :text：匹配所有单行文本框
  :password：匹配所有密码文本框
  其他表单元素类似
  ```
  + 表单对象属性：
  ```
  :enabled：匹配所有可用元素
  :disabled：匹配所有不可用元素
  :checked：匹配所有选中的被选中元素(复选框、单选框等，不包括select中的option)
  :selected：匹配所有选中的option元素
  ```
  [jQueryAPI1.4](E:\Github\StudyNotes\js文档\jQueryAPI1.4.chm)

4. 事件：

  ![图片](E:\Github\StudyNotes\Picture\JQ事件.png)

5. 属性：
  + 属性
  ```
  attr(name)
  attr(properties)
  attr(key,value)
  ```
  + CSS类：
  ```
  addClass(class|fn)
  removeClass([class|fn])
  toggleClass(class)
  ```
  + HTML代码/文本/值
  ```
  html()--需要带标签
  text()
  ```
6. 文档处理：
  + 内部插入：
  ```
  在内部结尾追加：
  A.append(B)--A中插入B
  A.appendTo(B)--B中插入A
  在内部开头追加：
  A.prepend(B)--向A的元素内部前置内容B。
  A.prependTo(B)--向B的元素内部前置内容A。
  ```
  + 外部插入：
  ```
  after(content)--将B追加到A后面
  before(content)--将B追加到A前面
  insertAfter(content)--将A追加到B后面
  insertBefore(content)--将A追加到B前面
  ```
  + 删除
  ```
  empty()--清空标签里的内容
  reomve([expr])--清空包括标签的内容
  ```
  + 复制：
  ```
  clone()
  clone(true)--副本也有相同的作用
  ```
  + 替换：
  ```
  A.replaceWith(B)--用B替换A
  A.replaceAll(B)--用A替换B
  ```
