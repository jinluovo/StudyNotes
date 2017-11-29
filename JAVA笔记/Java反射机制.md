# Java反射机制（Java Reflection）
[参考文章](https://github.com/DreamYHD/StudyNotes/blob/master/Java/Java%20%E5%8F%8D%E5%B0%84.md)

参考书籍：《疯狂Java讲义》（第3版）

Java程序中许多对象在运行时都会出现两种类型：编译时类型和运行时类型。为了在运行时发现对象和类的真实信息，可以有一下两种方法：
+ 如果在编译时和运行时都完全知道类型的具体信息，可以先使用`instanceof`运算符进行判断，再利用强制类型转换将其转换成其运行时类型的变量即可。
+ 如果编译时根本无法预知该对象和类可能属于哪些类，程序只能依靠运行时信息来发现该对象和类的真实信息，这就必须要用到**反射**。

### 定义
Java反射机制是指在运行状态中，对于任意一个类，都可以知道这个类的所有属性和方法；对于任意一个对象，都能够调用他的任意方法和属性；这种动态获取信息以及动态调用对象方法的功能称为Java语言的反射机制。
### 运用
##### 获得Class类对象（3种）
由于每个类被加载之后，系统就会为该类生成一个对应的Class对象，通过该Class对象就可以访问到JVM中的这个类。在Java程序中获取Class对象通常可以有以下三种方式：
+ 使用Class类的forName(String clazzName)静态方法。该方法需要传入字符串参数，该字符串参数的值是某个类的全限定类名
```Java
Class pClass = Class.forName("com.indi.jinlu.Reflection.People");    //可能会抛出ClassNotFoundException异常
System.out.println(pClass.getSimpleName());
```
运行结果：
```
People
```
+ 调用某个类的class属性来获取该类对应的Class对象。
```Java
Class pClass2 = People.class;   //编译阶段即可检查需要访问的Class对象是否存在
System.out.println(pClass2.getName());
```
运行结果：
```
com.indi.jinlu.Reflection.People
```
+ 调用某个对象的getClass()方法。该方法是 java.lang.Object 类中的一个方法，所有的java对象都可以调用该方法，该方法将返回该对象所属类对应的Class对象。
```Java
People p = new Chinese();
Class pClass3 = p.getClass();
System.out.println(pClass3.getName());
```
运行结果：
```
com.indi.jinlu.Reflection.Chinese
```

#### 创建对象（2种）
+ 使用Class对象的newInstance()方法来创建该Class对应类的实例，这种方式要求该Class对应类有默认构造器，而使用newInstance()方法实际上是利用默认构造器来创建该类的实例。
```Java
People p1 = (People) pClass1.newInstance();
p1.setAge(20);
System.out.println(p1.getAge());
```
运行结果：
```
20
```
+ 先使用Class对象获取指定的Constructor对象，再调用Constructor对象的newInstance()方法来创建该Class对象对应类的实例，通过这种方式可以选择使用指定的构造器来创建实例。
```Java
Constructor constructor = pClass2.getConstructor(int.class,String.class);//获取制定参数类型的构造器
People p2 = (People) constructor.newInstance(17,"Chinese");
System.out.println(p2.getAge() + p2.getCountry());
```
运行结果：
```
17Chinese
```

#### 获取方法
+ getDeclaredMethods()返回类或接口声明的所有方法，包括public、protected、friendly、private，但不包括继承的方法
```Java
Class cClass1 = Chinese.class;
Method[] methods = cClass1.getDeclaredMethods();
for (Method m:
    methods) {
  System.out.println(m);
}
```
运行结果：
```
public void com.indi.jinlu.Reflection.Chinese.run()
protected void com.indi.jinlu.Reflection.Chinese.weight()
private void com.indi.jinlu.Reflection.Chinese.age()
void com.indi.jinlu.Reflection.Chinese.say()
```
+ getDeclaredMethod(String name,Class<?>...parameterTypes)返回此Class对象对应类的、带指定形参列表的方法，与方法的访问权限无关。
```Java
Class cClass4 = Chinese.class;
Method method1 = cClass4.getDeclaredMethod("set", int.class, String.class);
System.out.println(method1);
```
运行结果：
```
private void com.indi.jinlu.Reflection.Chinese.set(int,java.lang.String)
```
+ getMethods()返回某个类的所有public方法，包括其继承类的public方法
```Java
Class cClass2 = Chinese.class;
Method[] methods1 = cClass2.getMethods();
for (Method m:
     methods1) {
    System.out.println(m);
}
```
运行结果：
```
public void com.indi.jinlu.Reflection.Chinese.run()
public java.lang.String com.indi.jinlu.Reflection.People.getCountry()
public void com.indi.jinlu.Reflection.People.setCountry(java.lang.String)
public int com.indi.jinlu.Reflection.People.getAge()
public void com.indi.jinlu.Reflection.People.setAge(int)
public final void java.lang.Object.wait() throws java.lang.InterruptedException
public final void java.lang.Object.wait(long,int) throws java.lang.InterruptedException
public final native void java.lang.Object.wait(long) throws java.lang.InterruptedException
public boolean java.lang.Object.equals(java.lang.Object)
public java.lang.String java.lang.Object.toString()
public native int java.lang.Object.hashCode()
public final native java.lang.Class java.lang.Object.getClass()
public final native void java.lang.Object.notify()
public final native void java.lang.Object.notifyAll()
```
+ getMethod(String name,Class<?>...parameterTypes)返回一个特定的方法
```Java
Class cClass3 = Chinese.class;
Method method = cClass3.getMethod("run",null);
System.out.println(method);
```
运行结果：
```
public void com.indi.jinlu.Reflection.Chinese.run()
```

#### 获取构造器信息：
获取构造器的方法与上述获取方法的用法类似，共有4种，通过getConstructor()方法得到Constructor类的一个实例，而Constructor类有一个newInstance()方法可以创建一个实例对象

#### 获取Class类对应所包含的成员变量
+ getField(String name)：返回此Class类对应类的、指定名称的public成员变量
+ getFields()：返回此Class类对应的所有的public成员变量
+ getDeclaredField(String name):返回此Class类对应类的、指定名称的成员变量，与成员变量的访问权限无关。
+ getDeclaredFields():返回此Class类对应类的成员变量，与成员变量的访问权限无关。

#### 访问Class类对应类上包含的所有的Annotation（注解）
+ getAnnotations()：返回修饰该Class对象对应类上存在的所有Annotation
+ getDeclaredAnnotations()：返回直接修饰该Class对象对应类上存在的所有Annotation

还有很多可以获取的信息不一一列举啦~~~

#### 调用方法：
获取Class的方法之后，可以使用invoke()方法来调用这个方法。invoke()方法原型为
```Java
public Object invoke(Object obj, Object... args)
        throws IllegalAccessException, IllegalArgumentException,
           InvocationTargetException
```
```Java
Class cClass4 = Chinese.class;
Method method1 = cClass4.getDeclaredMethod("set", int.class, String.class);
System.out.println(method1);
Chinese chinese = new Chinese();
method1.invoke(chinese,12,"China");
```
运行结果为：
```
public void com.indi.jinlu.Reflection.Chinese.set(int,java.lang.String)
with parameters age = 12,country = China
```
当通过Method的invoke()方法来调用对应的方法时，Java会要求程序必须有调用该方法的权限。如果程序确实需要调用某个对象的private方法，则可以先调用Method对象的如下方法。 setAccessible(boolean flag)：将Method对象的acessible设置为指定的布尔值。值为true，指示该Method在使用时应该取消Java语言的访问权限检查；值为false，指示该Method在使用时要实施Java语言的访问权限检查。
```Java
method1.setAccessible(true);      //该方法在使用时取消Java语言的访问权限检查
method1.invoke(chinese,12,"China");
```

#### 访问成员变量值：
+ getXxx(Object obj):获取obj对象的该成员变量值，此处Xxx对应8种基本类型。如果该成员变量的类型是引用类型，则取消get后面的Xxx。
+ setXxx(Object obj,Xxx val):将obj对象的该成员变量设置为val值。其余同get方法。

## 反射的优缺点：
**优点**：

  （1）能够在运行时动态的获取类的实例，大大提高了系统的灵活性和扩展性。

  （2）与Java动态编译结合，可以实现无比强大的功能

**缺点**：

  （1）使用反射性能较低

  （2）使用反射相对来说不安全

  （3）破坏了类的封装性，可以通过反射获取这个类的私有属性和方法。
