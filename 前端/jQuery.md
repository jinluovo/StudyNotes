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
