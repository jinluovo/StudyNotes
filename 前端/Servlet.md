## Servlet介绍：
1. Servlet是javaee的内容，是一个接口（interface）。Servlet是运行在Web服务器中的小型java程序，Servlet通常通过THHP（超文本传输协议）接受和响应来自Web客户端的请求（处理一个http请求，产生一个http响应）。
2. Servlet开发步骤：
  + 重写一个类继承HttpServlet（要实现此接口，可以编写一个继承`javax.servlet.GenericServlet`的一般Servlet，或者编写一个继承`javax.servlet.http.HttpServlet`的HTTP servlet。）
  + 重弄写方法doGet/doPost（根据请求提交方式get/post判断重写哪个方法）
  + 在web.xml文件中配置访问到Servlet的具体路径:
  ```xml
  <!-- 如果想要访问到Servlet程序，需要在web.xml中配置一个Servlet节点 -->
  <servlet>
  <servlet-name>hello</servlet-name>  <!-- 可以根据Servlet的业务逻辑任意取名字 -->
    <servlet-class>pack1.ServletHello</servlet-class>   <!--声明的Servlet的全路径-->
  </servlet>
  <servlet-mapping>
  <servlet-name>hello</servlet-name>    <!-- 要跟servlet节点下的servlet-name对应起来 -->
  <url-pattern>/hello</url-pattern>   <!-- 通过url-pattern来确定访问servlet的路径 -->
  </servlet-mapping>
  ```
3. Servlet的生命周期方法：
  + 生命周期：对象从创建到销毁
    + 构造servlet，然后使用init方法将其初始化。当servlet创建的时候会调用构造和init方法（只会调用一次），默认情况当web应用运行起来不会创建servlet对象，只有当有人访问servlet的时候才回创建。
    ```xml
    <!--可以在web.xml中配置如下-->
    <load-on-startup>1</load-on-startup>		<!-- 设定应用运行时即创建servlet对象 -->
    ```
    + service：当客户端向服务端发出一个http请求时，会调用service方法，service方法会获取请求的方式，根据不同的请求方式调用不同的doXXX()方法，doGet()/doPost()/doHead()/doDelete()/doTrace()/doOptins()/doPut()
    + destroy：当servlet被创建之后，servlet对象就会被缓存起来，知道服务器正常关闭servlet对象才回被销毁，销毁的时候会调用destroy方法
4. servlet配置文件url-pattern的几种写法：（以下几个条件同时满足时，优先级依次从上到下）
    + 完整路径匹配：
    ```xml
    <url-pattern>/webscyle</url-pattern>
    ```
    + 目录匹配：
    ```xml
    <url-pattern>/*</url-pattern>
    ```
    + 扩展名匹配：
    ```xml
    <url-pattern>.do</url-pattern>
    ```
5. 提交参数时的绝对路径和相对路径：（在真实开发环境中，一般使用绝对路径）
    + 绝对路径： 把访问到要提交参数的servlet的url地址截取服务器IP之后的路径，作为访问的绝对路径
    ```HTML
    <form action="/ServletHello/cbf" methond="get">
    ```
    + 相对路径：根据当前项目的目录结构，如果HTML网页与servlet访问路径在同一级目录，直接写servlet的url-pattern就可以了。如果HTML网页与servlet访问路径不在同一级目录，可以通过`../`返回上一级目录。
    ```HTML
    <form action="cbf" methond="get">
    ```
6. ServletConfig:
    + Servlet容器使用的servlet配置对象，该对象在初始化期间将信息传递给servlet
    + 通过ServletConfig可以获取与servlet相关的信息
    + 获取ServletConfig对象的方法步骤：
      + 获取ServletConfig对象：重写init()方法，在init方法中通过一个成员变量保存传入的ServletConfig，
      ```java
      @Override
      public void init(ServletConfig config) throws ServletException {
      	super.init(config);
      	this.config = config;
      }
      ```
      或者通过getServletConfig()方法获取ServletConfig对象
      ```java
      ServletConfig config2 = getServletConfig();
      ```
      + 通过ServletConfig获取初始化参数，在servlet节点下添加一个`<initParam>`节点
      ```xml
      <servlet>
      <servlet-name>hello</servlet-name>		
      <servlet-class>pack1.ServletHello</servlet-class>
      <init-param>
      <param-name>encoding</param-name>
      <param-value>UTF-8</param-value>
      </init-param>
      </servlet>
      ```
      通过servletConfig对象调用
      ```java
      String encoding = config.getInitParameter("encoding");
      ```
      通过此方法获取的初始化参数只对当前servlet有效
7. ServletContext:
  + 每一个servlet应用程序都对应着唯一一个ServletContext，这个ServletContext跟整个Servlet的生命周期保持一致，web应用创建，ServletContext创建，web应用销毁，ServletContext销毁
  + 获取ServletContext对象：
  ```java
  ServletContext context = config.getServletContext();		//通过ServletConfig对象获取
	ServletContext context1 = getServletContext();		//直接通过方法获取
  ```
  + 通过ServletContext可以在不同的Servlet之间传递参数：      
  可以在A Servlet中调用方法：
  ```java
  context.setAttribute("p", "hello");
  ```
  在任何Servlet中都可以通过p来获取到相应的内容
  ```java
  ServletContext context = config2.getServletContext();
	String Attritube = (String)context.getAttribute("p");
	System.out.println(Attritube);
  ```
  + 通过ServletContext可以获取在web.xml中配置的全局参数：
  ```xml
  <context-param>
  <param-name>encoding</param-name>
  <param-value>iso-8859-1</param-value>
  </context-param>
  ```
  获取全局参数的方法：
  ```java
  String Encoding = context.getInitParameter("encoding");
  ```
8. 通过HttpRequest获取跟请求相关的信息：
  ```java
  String method = request.getMethod();//获取请求的方法
	String protocol = request.getProtocol();//获取请求使用的协议
	String requestURI = request.getRequestURI();//获取请求的路径
	System.out.println("method=" + method + " protocol=" + protocol + " requestURI=" + requestURI);

	String username = request.getParameter("username");
	System.out.println(username);
	String[] hobbies = request.getParameterValues("hobby");
	for(String stemp:hobbies){
		System.out.println(stemp);
	}
  ```
9. Servlet可能遇到的中文乱码问题：
  + 产生乱码的原因：Tomcat默认采用的编码方式为`iso-8859-1`，这个字符集中没有中文字符
  + 处理response乱码：
    + 设置当前的输出流采用utf-8
    ```java
    response.setCharacterEncoding("utf-8");
    ```
    + 通知客户端，使用utf-8进行解码（通过设置响应头实现）
    ```java
    response.setHeader("ContentType","text/html;charset=utf-8");
    ```
    + 可以通过一行代码实现上面两行的效果
    ```java
    response.setContentType("text/html;charset=utf-8");
    ```
  + 处理request乱码：
    + post方式处理比较简单，参数都是通过请求提交上来的，可以通过方法设置请求体使用的编码集
    ```java
    //这个方法只对请求体有效
    request.setCharacterEncoding("utf-8");
    String parameter = request.getParameter("param");
    ```
    + get方式，由于参数是通过url地址拼接来的，上述方法对get方式没有效果，提交中文参数到url地址栏，都会先进行url编码，把中文的内容按照网页上传入的字符集进行编码获取到bye数组的内容放到地址栏上，提交到Tomcat服务器后
    ```java
    String parameter = request.getParameter("param");//默认使用iso-8859-1
    //还原成二进制
    byte[] temp = parameter.getBytes("iso-8859-1");
    //拿着二进制使用utf-8重新编码
    parameter = new  String(temp,"utf-8");
    ```
    + 如果涉及到中文内容需要提交，建议使用post方式提交
