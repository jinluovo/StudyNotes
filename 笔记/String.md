### String类：
* 内容具有不可变性

### StringBuffer类
* 可变性
* 实现线程安全

### StringBulider类：（优先考虑）
* 可变性
* 未实现线程安全

### Data类：
* java.util.Date
* 获取当前时间
```java
        Date d = new Date();
	    System.out.println(d);
      //默认格式： Wed Apr 26 21:43:22 CST 2017
```
  * 日期时间格式转换：java.text包中的SimpleDateformat类中的format()方法,代码中的 “yyyy-MM-dd HH:mm:ss” 为预定义字符串， yyyy 表示四位年， MM 表示两位月份， dd 表示两位日期， HH 表示小时(使用24小时制)， mm 表示分钟， ss 表示秒，这样就指定了转换的目标格式，最后调用 format() 方法将时间转换为指定的格式的字符串。
```java
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
String today = sdf.format(d);
//转换后的格式： 2017-04-26 21:52:36
```
  * 使用 parse() 方法将文本转换为日期：
    *  调用该方法时会出现转换异常，即ParseException，需进行异常处理（```import java.text.ParseException;```）

### Calendar类：
* java.util.Calendar 类是一个抽象类，可以通过调用 getInstance() 静态方法获取一个 Calendar 对象，此对象已由当前日期时间初始化，即默认代表当前时间。
```java
//		创建Calendar对象：
		Calendar c = Calendar.getInstance();
		int year = c.get(Calendar.YEAR);
		int month = c.get(Calendar.MONTH) + 1;//获取月份加1，0表示一月份
		int day = c.get(Calendar.DAY_OF_MONTH);
		int hour = c.get(Calendar.HOUR_OF_DAY);
		int minute = c.get(Calendar.MINUTE);
		int second = c.get(Calendar.SECOND);
		System.out.println("当前时间"  + year + "-" + month + "-" + day + " " + hour
				 + ":" + minute + ":" + second);
```
* Calendar 类提供了 getTime() 方法，用来获取 Date 对象，完成 Calendar 和 Date 的转换，还可通过 getTimeInMillis() 方法，获取此 Calendar 的时间值，以毫秒为单位。
```java
    Date date = c.getTime();		//将Calendar对象装换为Date类
		Long time = c.getTimeInMillis();   //获取当前毫秒数
		System.out.println(date);
		System.out.println(time);
```

### Math类：
* 位于 java.lang 包中，包含用于执行基本数学运算的方法， Math 类的所有方法都是静态方法，所以使用该类中的方法时，可以直接使用类名.方法名
* 常用方法：

![Math](../Picture/Math.jpg)
