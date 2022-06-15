一.java基础

1.跨平台原理 在需要运行的java应用程序的操作系统上，安装操作系统对应的JVM即可

2.JRE java运行环境

3.JDK java 程序开发工具包

 4.javac(.java=>class) java 运行

5.注释 // /**/ /*** / 

6.关键字 

7.空常量不能输出

​	常量的分类:字符串常量 整数常量 小数常量 字符常量 布尔常量 空常量

8.数据类型

​	数值型 整数 浮点数 字符 非数值型 布尔  引用型数据类型 类 接口 数组

byte 1 short 2 int 4

long 8 float 4 double 8 char 2 boolean 1

9.在程序中数据中可以发生变化的称为变量

int a = 20; a =21;

long类型的数据要加l

float类型的数据要f

10.标识符命名规则

不能以数字开头不能是关键字 区分大小写

由数字/字母/下划线和$符组成

大驼峰和小驼峰命名法

11.类型转换

自动类型转换 小范围到大范围

强制类型转换 大范围到小类型

运算符 + - * /  %

表达式的类型自动提升为表达中操作等级最高的类型

12 ""+ +是字符拼接符

13 += 是隐含了强制类型转换 

14 i++ 变量先做++ 

++i 先参与操作

15.==  != >= > < <=   

16.& | ^ !                       &&() || (有短路效果 执行的效率会高于前方)

17.三元运算符 a>b ? a:b;

17.数据输入

```java
 Scanner sc  = new Scanner(System.in);
    int a = sc.nextInt();

```

流程控制: 顺序结构  if 结构   if else结构 if ...else...if 结构 

switch结构

```java
public class SwitchTestDemo {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int week =sc.nextInt();
        switch (week){
            case 1:
                System.out.println("星期一");
                case 2:
                System.out.println("星期一");
                case 3:
                System.out.println("星期一");
                case 4:
                System.out.println("星期一");
                case 5:
                System.out.println("星期一");
                case 6:
                System.out.println("星期一");
                case 7:
                System.out.println("星期一");
            default:
                System.out.println("输入错误");
        }
    }
```

循环结构 for循环语句

```
public class SXH {
    public static void main(String[] args) {



        for (int i = 100; i <1000; i++) {
            int ge=i%10;
            int shi=i/10%10;
            int bai=i/100%10;
            if (ge*ge*ge+shi*shi*shi+bai*bai*bai==i){
                System.out.println(i);
            }
        }
    }
}
```

while（）{} 先判断条件

do{}while() 先执行一次

for变量不能在使用了

break；跳出循环了

continue :跳过某一次循环 不跳出循环 

嵌套循环：

```java
public class For_99 {
    public static void main(String[] args) {
        for (int i = 1; i <=9; i++) {
            for (int j = 1; j <=i ; j++) {
                System.out.print(i*j+"="+j+"*"+i+"\t");
            }
            System.out.println();
        }

    }
}
```

random

```java
Random r = new Random
    
```

数组

int [] arr 

int arr[]

int [] arr = new int[3];

arr[0]

栈内存:存储局部变量 使用完了之后立即消失

堆内存：new 出来的  每一个new出来的东西都有一个地址值 会在垃圾回收器空闲时被回收

数组案列

寻找数组中的最小值

```java
public class ArrDemo {
    public static void main(String[] args) {
        int [] arr = {1,2,7,3,11,};
        int max =arr[0];
        for (int i = 0; i <arr.length; i++) {
        if (max<arr[i]){
            max = arr[i];
        }
        }
        System.out.println(max);
    }
}

```

2.方法重载定义

```text
多个方法在同一个类中
方法的名字相同
传入的参数数量不同类型不同参数不同
```

3.数组遍历

```java
public class ArrDemo2 {
    public static void main(String[] args) {
        int[] arr = {1,2,1,41,4,1312,123};
        printArr(arr);
    }
    public static void printArr(int [] arr){
        System.out.print("[");
        for (int i = 0; i < arr.length; i++) {
            if (i==arr.length-1){
                System.out.print(arr[i]);
            }else {
            System.out.print(arr[i]+",");
        }
        }
        System.out.println("]");
    }
}
```

类和对象

类:对生活中有共同特性和行为的事务的抽象

对象：是类的实体

封装private（隐藏成员变量信息）

```text
面向对象的三大特征之一
是面向对象编程语言对客观世界的模拟，客观世界里的成员变量都是隐藏在对象内部的，外界只能提供该类提供的方法对隐藏信息进行操作和访问
提高了代码的安全性和复用性
```

this：局部变量和成员变量重名的时候使用

API：应用编程接口

```java
public class APIDemo {
    public static void main(String[] args) {
Scanner sc = new Scanner(System.in);
        String line = sc.nextLine();
        System.out.println(line);
    }
}
```

String

```text
字符串不可变，但是他的值在创建后不能被更改
他们的值是可以被共享的
底层byte[]
String s="" 在常量池的空间中
String s = new String(); 有地址的
String.equals();
String.length();
String.charAt(int index);
```

StringBuilder

```text
String 的内容不可变
StringBulider的内容可变
StringBuilder sb = new StringBuilder();
StringBuilder sb = new StringBuilder("hello");
sb.append("") 添加
sb.reverser();反转
sb.toString();
StringBUilder sb =  new StringBuilder(s);
```

ArrayList<E>

```text
ArrayList<String> array = new ArrayList<String>();
array.add(E e );
array.add(int index,E e)
array.size();
array.get(int index);
array.remove(Object o);
array.remove(int index);
array.set(int index,E element);
```

extends

```text
提高代码的复用性
提高的代码的维护性
让类与类之间产生的关系类的耦合性增加
```

super

```text
super的用法与this相似
super代表父类的存储空间的标识
```

方法重写

```text
子类中出现和父类一样的方法声明
@Override
父类的私有方法是不能被重写的（私有成员不能被继承）
支持单继承不支持多继承
支持多层继承
```

package

```text
就是文件夹 对类进行管理分类
```

import 

```text
格式 import 包名;
```

修饰符

```text
private
public 
protected
```

状态修饰符

```tetx
final 修饰方法 最终方法不能被重写 修饰变量表面改变量是常量，不能被赋值，修饰类，不能被继承，修饰引用类型的地址值不能发生改变 内容可以发生改变

static(静态) 被类的私有对象共享的 可以通过类名调用 静态的成员方法只能访问静态成员
```

多态

```tetx
有继承和实现关系
有方法重写
有父类引用指向字类
编译看左边，执行看右边
好处:提高了编程的扩展性
不能使用子类特有的功能（new 字类）
向上转型:子到父自动类型转换 父到子 向下转型是强制类型转换
```

abstract

```text
抽象类和抽象方法必须使用abstract
抽象类不一定有抽象方法 有抽象方法的一定是抽象类
不能实列化
成员变量可以是变量也可以是常量
有构造方法，但是不能被实列化 用于子类访问父类数据的初始化
可以有抽象方法 用于限制字类必须完成某一些动作
也可以有非抽象方法，提高代码的复用性
```

接口

```text
公共的规范标准
对行为的抽象
interface
implements
多态（）
必须重写接口中全部的抽象方法
成员变量只能是常量
成员方法只能是抽象方法
接口与类的关系多实现
接口与接口是继承关系
```

抽象类和接口的抽象

```tetx
抽象类是对事务的抽象 而接口是对行为的抽象
```

内部类

```text
在类中定义一个类
内部类的访问特点(可以直接访问外部类的成员包括私有成员 外部类访问内部类的成员必须创建对象)
成员内部类Outer.inner oi = new Outer().new Inner();
局部内部类：是定义在方法中的类，需要在方法内部创建对象并使用，该类可以直接访问外部类的成员，也可以访问方法内的局部变量
匿名内部类 new 类名或者是接口名 
匿名内部类在开发过程中的使用
```

```java
public class JumpDemo {
    public static void main(String[] args) {
        JumpOperator jo = new JumpOperator();
        jo.jump(new Jumpping() {
            @Override
            public void jump() {
                System.out.println("猪可以被吃了");
            }
        });
    }
}
public class JumpOperator {


    public void jump(Jumpping j) {
j.jump();
    }
}

package com.pinkhat.day1.nbl;

public interface Jumpping {
    void jump();
}

```

常用apiMath

```text
Math.abs(int a);
Math.ceil(double a);
Math.floor(double a);
Math.round(float a);
Math.max(int a,int b);
Math.min(int a,int b);
Math,pow(double a,double b);
Math.random();
```

System类

```text
System.exit(int a);
System.currentTimeMillis();

```

Object

```text
Object.toString();
Object.equals();
```

冒泡排序

```java
public class MPDemo {
    public static void main(String[] args) {
        int [] arr = {1,2,5,22,3,99,111,231,1551,12312,};
        String s = arrayToString(arr);
        System.out.println(s);
        for (int i = 0; i <arr.length-1 ; i++) {
            for (int j = 0; j <arr.length-1-i ; j++) {
                if (arr[j]>arr[j+1]){
                    int temp = arr[j];
                    arr[j]=arr[j+1];
                    arr[j+1]=temp;
                }
            }
        }
        String s1 = arrayToString(arr);
        System.out.println(s1);
    }

    public static String arrayToString(int [] arr){

        StringBuilder sb = new StringBuilder();
        sb.append("[");
        for (int i = 0; i <arr.length ; i++) {
            if (i==arr.length-1){
                sb.append(arr[i]);
            }else {
                sb.append(arr[i]).append(",");
            }

        }
        sb.append("]");
        return sb.toString();
    }
} 

```

Arrays类

```text
Arrays.sort();
```

Integer类

```text
Interger i1 = new Integer(100);
new Integer("1");
Integer.valueof(100)； int=>string
parseInt(String s) string=>int 
自动装箱 
Integer i = 100;//自动装箱
i+=200; //自动拆箱
i= i+200;自动装箱
```

Date

```java
Date d1 = new Date();//long
d1.getTime();
d1.setTime();
```

SimpleDateFormat类

```java
SimpleDateFormat sdf = new SimpleDateFormat(String pattern);
sdf.format(Date d);
sdf.parse(String source);
```

Calendar类

```java
Calendar c1 =Calendar.getInstance();
c1,get(Calendar.YEAR);
c1,get(Calendar.MONTH);
c1,get(Calendar.DATE);
add(int field,int amount);
set(int year,int month,int date);
```

Exeception

```java
Error:
Exception:
RunTimeException
非RunTimeException
```

try {

}catch(Exception e){

}

```java
public class ExceptionDemo {
    public static void main(String[] args) {
        System.out.println("a");


        try {
            int arr[] = {1,2,3};
            System.out.println(arr[4]);
        }catch (ArrayIndexOutOfBoundsException e){
            System.out.println(e.getMessage());
        }
        System.out.println("b");
    }
}


```

编译异常和运行时异常

throws处理异常:处理些没有权限进行处理的异常

集合体系:Collection

单列集合：List ArrayList<> LinkedList<>  Set HashSet<> TreeSet<> Map HashMap<>

```java
Collection<String>() c = new ArrayList<String>();
c.add(E e);
c.remove(Obeject o);
c.clear();
c.contains(Object o);
c.isEmpty();
c.size();
```

List集合特点:有序/可重复

```java
List<E> list = new ArrayList<E>();
list.add(int index,E element);
list.remove(int index);
list.set(int index,E element);
list.get(int index);
```

增强for循环

```java
for (E e list){
    System.out.println(e);
}
```

list集合的遍历方式

1.迭代器,集合特有的普遍遍历方式

2.普通for，带有索引的遍历方式

3.增强for，最方便的遍历方式

数据结构栈/队列

栈：先进后出

队列:先进先出

数组:查询效率高 删除效率低 ArrayList

链表:增删快，查询慢 LinkList

LinkList的特有功能

```java
list.addFirst();
list.addLast();
list.getFirst();
list.getLast();
list.removeFirst();
list.removeLast();
```

Set集合 没有重复元素 没有索引的方法，不能使用普通for循环

Hash值 ：JDK 根据对象的地址或者字符串或者数字算出int类型的数值

Object.getHashCode();

HashSet<E>

```tetx
1.底层数据结构的哈希表
2.对集的迭代顺序不作任何保证
3.没有索引
4.不包含重复的元素
```

哈希表：数组+链表

LinkedHashSet<E>集合的特点

```text
1.具有可预测的迭代次序
2.由链表保证元素有序，也就是说元素的存储和取出顺序是一致的
3.由哈希表保证元素的唯一性，也就是说没有重复的元素
```

TreeSet

```text
1.元素有序，按照一定的规则排序
2，没有索引
3.不能包含重复元素
```

自然排序Comparable

```java
自然排序，让元素所属的类实现Compareble接口，重写compareTo(T o)方法
    排序必须按主要条件和次要条件进行排序
```

泛型：参数化类型：在使用和调用的时候才传入具 体的类型

泛型类

```java
public class Generic<T>{
    private T t;
    get/ set
        public void show(T t){
        System.out.println(t);
    }
}
```

```java
public interface Genteric<T>{
    void show(T t);
}
```

类型通配符

```java
List<?>
    List<? extends Number>上限
    List<? super Number>下限
```

可变参数

```java
int... a
    Set.of("","","");
```

可变参数的使用

```text
Arrays.asList("","","",""); 不能使用删除和添加
List.of("","","");
Set.of();
```

Map集合

```text
Map<K,V> 将值映射到对象，不能包含重复的键，每一个键可以映射到最多一个值
创建Map集合的对象
多态的方式
具体的实现类是HashMap<K,V>
```

Map的基本功能

```java
Map<K,V> map = new HashMap<K,V>();
map.put();
map.remove();
map.clear();
map.containsKey();
map.containsValue();
map.isEmpty();
map.size();
map.get(Object key);
map.keySet();
map.values();
map.entrySet(); 
```

Map遍历的方式

1,基于keySet()方法实现

2.增强for实现

3.用get(Object key)实现

Collections实现

```text
Collections.sort(list);
Collections.reverse(list);
Collections.shuffle(list);
```

递归

```java
public class DiGuiDemo {
    public static void main(String[] args) {
        System.out.println(f(20));
    }
    public static int f(int n){
        if (n==1||n==2){
            return 1;
        }
        return f(n-1)+f(n-2);
    }
}

```

对象序列化流

```java
一个对象想要被序列化，该类对象必须实现Seriallzable接口
```

Properties集合

```java
Properties prop = new Properties();
prop.keySet();
prop.put();
prop.getProperty();
prop.stringPropertyNames();
```

线程

```text
1.概念：单个顺序控制流
2.多线程：进程有多条执行路径
3.实现方式：继承Thread类//实现Runable接口
mt.run();//
mt.start();
mt.setNmae();//设置线程名称
mt.getName();//返回线程名称
通过构造方法也可以设置线程名称
mt.currentThread();//返回当前正在执行的线程对象的引用
mt.setPriorty(int i);//设置线程优先级
mt.getPriorty();//获得线程优先级
mt.sleep(long millis)线程停止执行
mt.join()等待线程死亡
setDaemon(boolean on) 将线程标记为守护线程

```

线程同步问题

```\
同步代码块解决数据安全问提 
    private Object obj = new Object();
    synchronized(obj){
   
    }
    解决了多线程的数据安全问题
    当线程很多的时候每一个线程都会判断同步上的锁，很耗费资源的，降低程序的运行效率

 
```

 同步方法解决数据安全问题

```java
同步方法:就是把synchronized关键字加到方法上
public synchronized void sellTicket(){

}
同步静态方法
public static synchronized void sellTicket(){
    
}
静态的同步方法是SellTicket.class
```

线程安全的类

```text
StringBuffer

Vector

Hashtable
```

同步Lock锁

```java
private Lock lock = new ReentrantLock();
try{
    lock.lock();
}finally{
    lock.unlock();
}
```

网络编程

```java
网络编程三要素 IP地址 端口 协议
    ipconfig
    ping
    127.0.0.1
    InetAddress address = new InetAddress;getName("192.168/1.66")
Tcp:面向连接的通信协议
    可靠无差错的数据传输
    三次握手
    DatagramSocket ds = new DatagramSocket();
DatagramPacket(byte[]buf,int length,InetAddress address,int port)
    ds.send(DatagramPacket p);
ds.close();
接收数据
    DatagramSocket(int port)
    DatagramPacket(....)
    ds.receive(p)
    ds.close
```

TCP

```java
Socket(...)
    OutputStream.getOutputStream();
s.close()；
    
    
    ServerSocket(int port)
    .accept();
	getInputString
        .close
```



反射

```text
类的加载：将.class文件读入内存
类的连接：
类的初始化:
```

```java
public class ClassLoaderDemo {
    public static void main(String[] args) {
        ClassLoader c = ClassLoader.getSystemClassLoader();
        System.out.println(c);
        ClassLoader parent = c.getParent();
        System.out.println(parent);
        ClassLoader parent1 = parent.getParent();
        System.out.println(parent1);
    }
}

```

```text
运行时获取类的变量和方法信息 通过获取的信息来创建对象，在运行期可以扩展
```

获取类

```java
Student.class==s.getClass==Class.forName("path");
```

获取构造方法

```java
Constructor<?> con= c.getConstructors();//获取构造函数方法对象
c.getDeclareContructors();//获取私有的构造函数
con.setAccessible(true);
 Object obj =con.newInstance();//创建类对象
```

反射获取成员变量

```java
Class<?>c=Class.forName("path");
Filed[] fileds = c.getField();//获取成员变量//getDeclareField();
Field StringFiled = c.getField("String");
Constructor<?> con  = c.getConstructor();
Object o = con.getnewInstance();
stringFiled.set(o,"西安");

```

反射获取成员方法并使用

```java
Class<?> c =Class.forName("path");
Constructor<?> con = c.getConstructor();
Object obj =con.newInstance();
Method m1 =c.getMethod("");
m1.invoke(obj,"");

```



