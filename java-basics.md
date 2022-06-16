<h5>1.java语言的特性

开源，免费，面向对象，跨平台

java不支持多继承，C++支持

C++有指针的概念，Java屏蔽了指针的概念

Java是由C++实现的

Java的生态很好

面向对象，更符合人的思维模式，其复用性拓展性，可移植性也大大提高。

支持多线程

健壮性，有自动回收垃圾的机制



<h5>2.java的加载与执行

.java的源程序通过编译成字节码文件.class文件，再通过类加载器加载到虚拟机，由java虚拟机将.class文件编译成二进制文件与操作系统打交道，再由操作系统执行二进制与底层硬件系统交互。



<h5>3.classpath

如果没有指定classpath的话，那么它会默认为当前位置为classpath

 

<h5>4.BigDeciaml详解

为了避免极大丢失，可以使用BigDecimal来进行浮点数的运算

浮点数与浮点数之间的等值判断，基本数据类型不能用==来比较，包装数据类型不能用equals来判断

使用BigDeciaml时，应该使用BigDecimal(String val)构造方法或者BigDecimal.valueOf(double val) 的静态方法来构造



<h5>5.字符串常量和字符型常量的区别

字符常量是由单引号引起来的一个字符串，相当于一个整型值，可以参加运算表达式，只占2个字节

字符串常量是由双引号引起的一个或者多个字符，字符串常量通常是代表宇哥字符串在内存中存储的位置。占若干个字节

<h5>6.静态方法为什么不能调用非静态成员

静态方法属于类，在加载类的时候就会分配空间。可以通过类名直接访问，而非静态是属于实列对象的，通常通过类的实列对象去访问，在java中类的非静态成员在不纯在的时候静态成员静态方法就已经存在了，此时调用内存中还不处在的非静态成员遍历，属于非法操作(李靖邀请岳飞当偏将)

在调用方法的时候有何不同

调用的时候静态方法通常是类名.方法名的方式，也可以采用对象名。方法名在调用实列方法的时候只能采用对象名.方法名

静态方法只能访问金泰成员，实列方法即能访问成员变成，也能访问静态变量



<h5>可变参数

一个方法可以接收0个或者多个同样类型的参数

语法:method(String ...  args)

可变参数只能作为函数的最后一个参数

遇到方法重载会优先匹配固定参数的方法。



<h5>基本的数据类型

8种基本的数据类型

6钟数字型

4钟数字类型:byte,short int long

浮点型:float,double

一种字符型char

一种boolean

在long数据类型后面一定要加l，否则将作为整数去解析。

成员变量不赋值就是null，而基本类型有默认值且不是null。

包装类可以用为泛型，基本类型不可以

基本类型的局部变量存放在Java虚拟机栈中的局部变量表中，基本数据类型的成员变量放在Java虚拟机中的堆中，包装类型属于镀锡类型，我们知道几乎所有的对象占用实列都存在于堆中。

相比较于对象类型，基本数据类型占用的内存空间非常小





<h5>自动拆箱和装箱

装箱:将基本数据类用他们对应引用类型包装起来

拆箱:将包装类型转换为基本数据类型

```java
Integer i = 10;  //装箱
int n = i;   //拆箱
```

频繁的装箱和拆箱操作将严重影响系统的性能。



<h5>面向对象和面向过程的区别

面向过程是把解决问题的过程拆解为一个个方法，通过一个个方法的执行解决问题

面向对象会先抽出对象，然后用对象执行方法的方式解决问题

面向的对象的程序一般更易维护，易复用，易拓展。



<h5>成员变量于局部变量的区别

语法上:成员变量是属于类的，而局部变量是在代码块或者方法中定义的变量或是方法的参数，成员变量可以被public，private，static等修饰符修饰，而局部变量是不能被static修饰，当时成员变量和局部变量都能被final修饰。

存储方式，成员变量是存储在堆内存中，局部变量是存储在栈内存中，

生存时间，成员变量是对象一部分，它随着对象的存在而存在，局部变量是随着方法的调用而自动生成，随着方法的接收而消亡。

默认成员如果没有被赋值，则会以类型的默认值而赋值，而局部变量不会被赋值。



<h5>对象的相等和引用相等的区别

对象的相等一般比较的是内存中存放的内容是否相等。

引用相等一般是他们执行的内存地址是否相等。



<h5>类的构造方法有什么作用
构造方法是一个特殊的方法，它主要完成对象的初始化工作。





<h5>如果一个类没有声明构造方法，该程序能正确执行吗?

如果一个类没有声明构造方法，也可以执行，因为回有一个无参构造。如果一个类添加了一个有参构造，java就不会再添加默认的无参构造，如果重载了有参构造方法，记得要把无参构造方法写出来。



<h5>构造方法有哪些特点？是否可被override

无参构造方法特点如下

名字与类名相同，没有返回值，当时不能用void声明构造函数。生成类的对象时自动执行，无需调用。

构造方法不能被override重写，但是可以被overload(重载)，所以你可以看到一个类有多个构造函数的情况。



<h5>面向对象的三大特征

封装，继承，多态

封装是把一个对象的状态信息隐藏再对象内部，不允许外部对象直接访问到内部的信息。但是可以提供一些可以被外界访问的方法来操作属性。

继承：不同类型的对象，经常会有共同的特征，继承是再已存在内的定义作为基础创建新的类。新类可以添加的新的数据或功能，也可以用父类的功能。可以提高代码的重用，程序的可维护性，节省大量创建新类的时间，提高我们的开发效率。

父类的私有方法和私有属性是无法访问的。

子类可以对父类进行拓展。

子类可以用自己的方式实现父类的方法。

多态：

表示一个对象具有多个形态，具体表现为父类引用指向子类的实例。

继承/实现 重写方法，父类引用指向子类对象。

对象类型和引用类型之间具有继承或者是实现的关系。

引用类型变量发出的方法调用的到底是哪一个类中的方法，必须再程序运行期间才能确定。

多态不能调用只在子类存在但再父类不存在的方法

如果子类重写了父类的方法真正执行的子类覆盖的方法，如果子类没有覆盖父类的方法，执行的父类的方法。



<h5>接口和抽象类的区别有什么共同点和区别。

共同点:

都不能被实列话，

都可以包含抽象方法

都可以由默认的实现方法。

区别：

接口主要对类的行为进行约束。抽象类强调的是代码的复用。

一个类只能单继承，可以多实现。

接口中的成员变量只能是public static final 类型的，不能修改且必须由初始值。而抽象类的成员变量可以再子类中被抽象赋值，是default修饰。





<h5>深拷贝和浅拷贝

浅拷贝:会再堆上创建一个新的对象。不够，如果员对象的内部的属性是引用型的话，浅拷贝会直接复制内部对象的引用地址，也就是说，拷贝的对象和员对象共用一个内部对象。

深拷贝:深拷贝会完全复制整个对象，包括对象所包含的内部对象。



<h5>Java 常见类

Object

是所有类的父类，它提供11个方法

```java
/**
 * native 方法，用于返回当前运行时对象的 Class 对象，使用了 final 关键字修饰，故不允许子类重写。
 */
public final native Class<?> getClass()
/**
 * native 方法，用于返回对象的哈希码，主要使用在哈希表中，比如 JDK 中的HashMap。
 */
public native int hashCode()
/**
 * 用于比较 2 个对象的内存地址是否相等，String 类对该方法进行了重写以用于比较字符串的值是否相等。
 */
public boolean equals(Object obj)
/**
 * naitive 方法，用于创建并返回当前对象的一份拷贝。
 */
protected native Object clone() throws CloneNotSupportedException
/**
 * 返回类的名字实例的哈希码的 16 进制的字符串。建议 Object 所有的子类都重写这个方法。
 */
public String toString()
/**
 * native 方法，并且不能重写。唤醒一个在此对象监视器上等待的线程(监视器相当于就是锁的概念)。如果有多个线程在等待只会任意唤醒一个。
 */
public final native void notify()
/**
 * native 方法，并且不能重写。跟 notify 一样，唯一的区别就是会唤醒在此对象监视器上等待的所有线程，而不是一个线程。
 */
public final native void notifyAll()
/**
 * native方法，并且不能重写。暂停线程的执行。注意：sleep 方法没有释放锁，而 wait 方法释放了锁 ，timeout 是等待时间。
 */
public final native void wait(long timeout) throws InterruptedException
/**
 * 多了 nanos 参数，这个参数表示额外时间（以毫微秒为单位，范围是 0-999999）。 所以超时的时间还需要加上 nanos 毫秒。。
 */
public final void wait(long timeout, int nanos) throws InterruptedException
/**
 * 跟之前的2个wait方法一样，只不过该方法一直等待，没有超时时间这个概念
 */
public final void wait() throws InterruptedException
/**
 * 实例被垃圾回收器回收的时候触发的操作
 */
protected void finalize() throws Throwable { }
```



<h5>== 和 equals()的区别

==对于基本类型和引用类型的作用是不同的；

对于基本的数据类型来说，==比较的是值，

对于引用数据类型来说，==比较的是对象的内存地址。



<h5>hashcode（）

hashcode()获取散列码，这个散列码的作用是确认该对象再hash表的索引位置。该方法通常就将该对象的内存地址转换为int类型返回。

hash表存储的是键值对kv，它的特点是能够工具键快速索引出对应的值。

```java
当你把对象加入 `HashSet` 时，`HashSet` 会先计算对象的 `hashCode` 值来判断对象加入的位置，同时也会与其他已经加入的对象的 `hashCode` 值作比较，如果没有相符的 `hashCode`，`HashSet` 会假设对象没有重复出现。但是如果发现有相同 `hashCode` 值的对象，这时会调用 `equals()` 方法来检查 `hashCode` 相等的对象是否真的相同。如果两者相同，`HashSet` 就不会让其加入操作成功。如果不同的话，就会重新散列到其他位置。这样我们就大大减少了 `equals` 的次数，相应就大大提高了执行速度。

其实， `hashCode()` 和 `equals()`都是用于比较两个对象是否相等。
```

hashcode 能够减少equal是方法的次数

地址值再转换为hashcode的过程中会产生hash碰撞，即hashcode一样，而对象不一样的情况。

两个相同对象的hashcode必须一致，如果equals方法判断两个对象是相等的hashcode值也必须相等。



<h5>String、StringBuffer、StringBuilder 的区别？

`String` 是不可变的 每一次后面加一个字符串都new String对象

StringBuffer、StringBuilder提供了修改字符串长度的方法。

线程安全性

`String` 中的对象是不可变的，也就可以理解为常量，线程安全。

StringBuffer再方法上加入了同步锁，所以是线程安全的。

StringBuilder每一加同步锁所以是非线程安全的。

性能:

相同情况下使用 `StringBuilder` 相比使用 `StringBuffer` 仅能获得 10%~15% 左右的性能提升，但却要冒多线程不安全的风险。

对于三种使用情况的总结

1. 操作少量的数据: 适用 `String`
2. 单线程操作字符串缓冲区下操作大量数据: 适用 StringBuilder
3. 多线程操作字符串缓冲区下操作大量数据: 适用 StringBuffer

intern 方法有什么作用?

String.intern() 是一个 native（本地）方法，其作用是将指定的字符串对象的引用保存在字符串常量池中，可以简单分为两种情况：



<h5>try-catch-finally如何使用

try块:用于捕获异常，其后可跟多个或者0个catch块，每一catch块，则必须跟一个finally块。

catch块:用于处理try捕获的异常。

finally块:无论是否捕获异常，finally块里面的语句都会执行。当try块或者catch块中遇到return语句时，finally语句块将再方法返回之前被执行。

不要在finally语句块中使用return，当try语句中和finally语句中都有return语句时，try中的return会被忽略，这是因为try语句中的retrun放回值先被存在本地变量中，当执行到finally语句中的return之后，本地变量的值就变为了finally语句中的return返回值

finally的代码块一定会执行吗？

不一定，比如说finally之前虚拟机终止运行的话，finally代码就不会执行。(程序所在的线程死亡关闭cpu)

不要把异常定义为静态变量，因为这样会导致异常栈信息错乱。每次手动抛出异常我们都需要手动new一个异常对象抛出，

抛出的消息一定要有意义，抛出的异常应该更具体。

使用日志打印了异常之后就不要抛出异常了。





<h5> 泛型：

泛型参数增强代码的稳定性以及可读性。

泛型的使用方法：

泛型类：泛型接口：泛型方法



项目中那些用到了泛型。

自定义接口通用的返回结果用到了泛型

定义Excel处理类ExcelUtils<T>用于动态指定Excel导出的数据类型。

构建集合工具类()



<h5>反射

它通过它获取任意的类的所有属性和方法和调用这些属性和方法的机制。

反射的应用场景

大多数的框架都是基于放射的原理

```java
public class DebugInvocationHandler implements InvocationHandler {
    /**
     * 代理类中的真实对象
     */
    private final Object target;

    public DebugInvocationHandler(Object target) {
        this.target = target;
    }

    public Object invoke(Object proxy, Method method, Object[] args) throws InvocationTargetException, IllegalAccessException {
        System.out.println("before method " + method.getName());
        Object result = method.invoke(target, args);
        System.out.println("after method " + method.getName());
        return result;
    }
}

```

注解也使用了反射。

注解的解析方法编译(@Overide)被扫面和运行(@Component)其通过反射处理



<h5>序列化(Serializable)

序列化:将数据结构转换为二进制流字节流的过程。

反序列化:将在序列化过程钟发所生成二进制字节流转换成数结够或者是对象的过程。

对于不想进行序列化的变量，使用transient关键字装饰。

不能修饰类和方法。

static不属于对象，所以无论有没有transient关键字修饰，均不会被序列化。



<h5>Java中的IO流

InputStream/Reader

OutputStream/Writer

既然有了字节流,为什么还要有字符流?

字符流方便我们堆字符进行流操作（因为可能不知道字符的编码格式）。





<h5>几个关键字

final: 关键字，意思是最终的、不可修改的，最见不得变化 ，用来修饰类、方法和变量

static：

j修饰成员变量和和成员方法。

​	静态代码块：静态代码块定义在类方法之外，静态diamond块在非静态代码块之前执行{静态代码块->非静态代码块->构造方法}。无论该类创建多少个对象，静态代码块只执行一次。

静态导包:用来导入类中的静态资源。可以直接使用该类的成员变量和成员方法。

静态内部类:它的创建不需要依赖外围内的创建，不能使用任何外围类的非staic的变量和方法。

this:指向当前的实列

super:用于从子类访问父类的变量和方法。



<h5>为什么 Java 中只有值传递

如果传递的是基本的类型的话，很简单，传递的就是基本类型的字面量值的拷贝，会创建副本。

如果参数是引用类型的话，传递的就是实参所用对象在堆中地址值的拷贝。



<h5>代理模式

  我们使用代理对象来代替真实对象的访问，这样我们在不修改原对象的前提下，提供额外的功能操作，扩展目标对象的功能。

代理模式的主要作用是扩展目标的功能，比如说在目标对象的某一个方法执行执行前后增加一些自定义操作。

静态代理和动态代理

静态代理:目标对象的每一个方法都是都得完成的；

​				静态代理在编译时将接口实现类，代理类都变成一个个实际的class文件。

静态代理实现步骤:

定义一个接口及其实现类；

创建一个代理类同样实现这个接口/

将目标对象注入进代理类，然后在代理类的对应订单调用目标类中的对应的方法。这样就可以通过代理类屏蔽掉目标对象的访问。并且可以在方法前后做一些增强。





<h5>动态代理

从JVM角度来说，动态代理是在运行时生成类的字节码，并加载到JVM中，

(SpringAOP RPC)

JDK动态代理和CGLIB动态代理

实现动态代理机制

在java动态代理机制中InvocationHandler接口和Proxy类是核心。

Proxy类中使用次数最高的方法是newProxyInstance()，这个方法主要用来生成一个代理对象。

```java
   public static Object newProxyInstance(ClassLoader loader,
                                          Class<?>[] interfaces,
                                          InvocationHandler h)
        throws IllegalArgumentException
    {
        ......
    }
```



这个方法有3个参数(loader：类加载器，interfaces：被代理类实现的一些接口， InvocationHandler h 实现了InvocationHadler接口的对象)

要实现动态代理的话，还必须要实现InvocationHandler来自定义逻辑，当我们的动态代理对象调用一个方法时，这个方法的调用就会被转发到实现InvocationHandler接口类的invoke方法来调用

```java
public interface InvocationHandler {

    /**
     * 当你使用代理对象调用方法的时候实际会调用到这个方法
     */
    public Object invoke(Object proxy, Method method, Object[] args)
        throws Throwable;
}
```



invoke（）方法有下面三个参数:
1.proxy：动态生成代理类。

2.method：与代理类对象调用用的方法相对应。

3.args：当前method方法的参数。

动态代理的实现步骤，

定义一个接口及其实现类:

自定义InvocationHandler并重写invoke(),在方法中我们会调用原生方法(被代理类的方法，并自定义一些二处理逻辑)

通过Proxy.newProxyInstance(ClassLoader loader,Class<?>[] interfaces,InvocationHandler h)方法来代理对象



invoke（）方法：当我们的动态代理对象调用原生方法的时候，最终实际上调用的invoke()方法。然后invoke()方法替代了我们去调用了被代理对象的原生方法。

获取代理对象的过程类

```java
public class JdkProxyFactory {
    public static Object getProxy(Object target) {
        return Proxy.newProxyInstance(
                target.getClass().getClassLoader(), // 目标类的类加载
                target.getClass().getInterfaces(),  // 代理需要实现的接口，可指定多个
                new DebugInvocationHandler(target)   // 代理对象对应的自定义 InvocationHandler
        );
    }
}
```

getProxy:主要是通过Proxy.newProxyInstance（）方法老获取代理对象。

CGLIB动态代理机制

JDK动态代理有一个致命的问题就是只能代理实现了接口类。

CGLIB是一个基于ASN的字节码生成库，它允许我们在运行时对字节码进行修改和动态生成。

CGLIB通过继承的方式实现实现代理，在SpringAop中如国目标对象实现了接口，则默认采用JDk动态代理模式，否则采用CGLIB模式。

在CGLIB动态代理机制中MethodInterceptor接口和Enhancer是类的核心。

你需要定义MethodeInterceptor（）并重写interxept方法，intercept用于拦截增强被代理类的方法。

```java
public interface MethodInterceptor
extends Callback{
    // 拦截被代理类中的方法
    public Object intercept(Object obj, java.lang.reflect.Method method, Object[] args,
                               MethodProxy proxy) throws Throwable;
}
```

1.obj：被代理的对象，需要增强的对象

2.method：被拦截的方法,增强的方法。

4.args:方法入参，

4.proxy：代理调用的原始方法

通过Enhancer类来动态获取被代理类，当代理类调用方法的时候，实际调用的是MethodInterceptor中的intercept方法。



CGLIB动态代理类的步骤；

定义一个类；

2，定义一个MethodInterceptor并重写intercept方法，intercept用于拦截增强被代理类的方法，和JDK动态代理中的invoke方法类似。

3.通过Enhancer类的create()创建代理类。



JDK动态代理和CGLIB动态代理对比。

JDK动态代理只能代理实现了的接口的类或者直接代理接口，而CGLIB可以代理未实现任何接口的类，另外CGLIB动态代理是通过生成一个被代理类的子类来拦截被代理类的方法调用，因此不能代理声明final类和方法，

大部分情况下，JDK动态代理的效率更高。







<h5>线程

进程?

进程是程序的一次执行过程。是系统运行程序的基本单位。

线程?

线程与进程相似，但是线程是一个比进程还小的执行单位，一个进程在器执行过程中可以产生多个线程。

多个线程共享进程的堆和方法区资源，但是每一个线程都有自己的程序计数器，虚拟机栈，本地方法栈。

线程被称为最轻量的进程。

一个java程序运行是main线程和多个其他线程间的运行。

进程是相互独立的，线程是会相互影响的，线程的开销小，当不利于资源保护，而进程相反

为什么要使用多线程呢

多核 CPU 时代意味着多个线程可以同时运行，这减少了线程上下文切换的开销。

利用多线程的机制可以大大的提高系统的并发能力及性能。

多线程带来的问题:

内存泄漏，死锁，线程不安全。

生命周期:创建 运行 阻塞 等待 超时 终止

线程创建之后它将处于 **NEW（新建）** 状态，调用 `start()` 方法后开始运行，线程这时候处于 **READY（可运行）** 状态。可运行状态的线程获得了 CPU 时间片（timeslice）后就处于 **RUNNING（运行）** 状态。

当线程执行 `wait()`方法之后，线程进入 **WAITING（等待）** 状态。进入等待状态的线程需要依靠其他线程的通知才能够返回到运行状态，而 **TIMED_WAITING(超时等待)** 状态相当于在等待状态的基础上增加了超时限制，比如通过 `sleep（long millis）`方法或 `wait（long millis）`方法可以将 Java 线程置于 TIMED_WAITING 状态。当超时时间到达后 Java 线程将会返回到 RUNNABLE 状态。当线程调用同步方法时，在没有获取到锁的情况下，线程将会进入到 **BLOCKED（阻塞）** 状态。线程在执行 Runnable 的`run()`方法之后将会进入到 **TERMINATED（终止）** 状态。

切换上下文?

线程在执行过程中会有自己的运行条件和状态，保存当前线程的状态，留待线程下次占用Cpu恢复线程，并加载到下一个将要占用cpu的线程上下文。

主动让出cpu，比如调用了sleep(),wait()

时间片用完，防止一个线程占用cpu的时间过长，

调用了阻塞类型的系统中断，比如请求I/O线程被阻塞，

被终止。

死锁:

多个线程被同时阻塞，它们中的一个或者多个都在等待某一个资源被释放，由于线程被无限期阻塞，因此程序不可能正常终止。

产生死锁的必要条件。

互斥条件，该资源任意时刻只由一个线程占用，

请求与条件保持，一个线程因请求资源而阻塞，对已获取的资源保持不放，

3。不能被剥夺条件，线程以获取的资源在位使用完之前不能·被其他线程剥夺，只有自己使用完毕后才释放资源

4.循环等待条件，若干个线程之间形成一种头尾相接的循环等待资源关系。

如何预防和避免线程死锁

1. **破坏请求与保持条件** ：一次性申请所有的资源。
2. **破坏不剥夺条件** ：占用部分资源的线程进一步申请其他资源时，如果申请不到，可以主动释放它占有的资源。
3. **破坏循环等待条件** ：靠按序申请资源来预防。按某一顺序申请资源，释放资源则反序释放。破坏循环等待条件。

 sleep() 方法和 wait() 方法区别和共同点

区别:sleep（）方法没有释放锁，wait方法释放锁

- 两者都可以暂停线程的执行。
- `wait()` 通常被用于线程间交互/通信，`sleep() `通常被用于暂停执行。
- `wait()` 方法被调用后，线程不会自动苏醒，需要别的线程调用同一个对象上的 `notify() `或者 `notifyAll()` 方法。`sleep() `方法执行完成后，线程会自动苏醒。或者可以使用 `wait(long timeout)` 超时后线程会自动苏醒。

为什么我们调用 start() 方法时会执行 run() 方法，为什么我们不能直接调用 run() 方法？

new 一个 Thread，线程进入了新建状态。调用 `start()`方法，会启动一个线程并使线程进入了就绪状态，当分配到时间片后就可以开始运行了。 `start()` 会执行线程的相应准备工作，然后自动执行 `run()` 方法的内容，这是真正的多线程工作。 但是，直接执行 `run()` 方法，会把 `run()` 方法当成一个 main 线程下的普通方法去执行，并不会在某个线程中执行它，所以这并不是多线程工作。

**总结： 调用 `start()` 方法方可启动线程并使线程进入就绪状态，直接执行 `run()` 方法的话不会以多线程的方式执行。



<h5>synchronozed

synchronized关键字解决的是多个线程之间访问资源的同步性，synchronized关键字可以保证被它修饰的方法或者是diamond块只有一个线程执行。

使用方式。

修饰实列方法，作用于当前对象实列枷锁，进入同步代码块之前要获得当前实列对象的锁，

修饰静态方法:也就是给当前类加锁，会作用于类的所有对象实例 ，进入同步代码前要获得 当前 class 的锁

修饰代码块：指定加锁对象，对给定对象/类加锁。`synchronized(this|object)` 表示进入同步代码库前要获得给定对象的锁。`synchronized(类.class)` 表示进入同步代码前要获得 当前 class 的锁.

synchronized` 关键字加到 `static` 静态方法和 `synchronized(class)` 代码块上都是是给 Class 类上锁。

synchronized` 关键字加到实例方法上是给对象实例上锁。

尽量不要使用 `synchronized(String a)` 因为 JVM 中，字符串常量池具有缓存功能！

单例模式了解吗？

```java
public class Singleton {
//但是由于 JVM 具有指令重排的特性，执行顺序有可能变成 1->3->2。使用 `volatile` 可以禁止 JVM 的指令重排，保证在多线程环境下也能正常运行。
    private volatile static Singleton uniqueInstance;

    private Singleton() {
    }

    public  static Singleton getUniqueInstance() {
       //先判断对象是否已经实例过，没有实例化过才进入加锁代码
        if (uniqueInstance == null) {
            //类对象加锁
            synchronized (Singleton.class) {
                if (uniqueInstance == null) {
                    uniqueInstance = new Singleton();
                }
            }
        }
        return uniqueInstance;
    }
}
```



构造方法本身可以就是线程安全的不存在同步构造方法一说。



<h5>volatile 关键字

volatile` 关键字 除了防止 JVM 的指令重排 ，还有一个重要的作用就是保证变量的可见性。

并发的三个特性:

```java
1. 原子性: 一次操作或者多次操作，要么所有的操作全部都得到执行并且不会受到任何因素的干扰而中断，要么都不执行。`synchronized` 可以保证代码片段的原子性。
2. 可见性 ：当一个线程对共享变量进行了修改，那么另外的线程都是立即可以看到修改后的最新值。`volatile` 关键字可以保证共享变量的可见性。
3. 有序性 ：代码在执行的过程中的先后顺序，Java 在编译器以及运行期间的优化，代码的执行顺序未必就是编写代码时候的顺序。`volatile` 关键字可以禁止指令进行重排序优化。
```

volatile和synchronized的区别

volatitle的线程同步的轻量级实现，所以volatile性能比synchronized关键字要好，但是volatile关键字只能用于变量而synchronized关键字可以修饰方法以及代码块。

valatile关键字能够保证数据的可见性，但不能保证数据的原子性。synchronized关键字两者都能保证。

valatile关键字解决的是变量在线程之间的可见性，而synchronized关键字解决的是多线程之间访问资源的同步性。





<h5>ThreadLocal

让每一个线程绑定自己的值，可以将ThreadLocal类形象的比喻程存在数据的盒子，盒子中可以存储每一个线程的私有数据。

如果你创建了一个ThreadLocal变量，那么访问这个变量的每一个线程都会有这个变量的本地副本。这也是ThreadLocal变量名的由来，它们可以使用get(),和set()方法来获取默认值或将其值更改位当前线程所存的副本的值，从而避免了线程安全问题。

内存泄漏问题

ThreadLocalMap中使用的key为ThreadLocal的弱引用，而value是强引用，所以，如果在ThreadLocal没有被外部强引用的情况下，在垃圾回收的时候，key会被清理，而value不会被清理，这样依赖，ThreadLocalMap中就会出现key为nukl的Entry，假如我们不做措施的话，value永远无法被GC回收，这个时候就可能会产生内存泄漏，ThreadLocalMap实现中已经考虑了这种请求，在调用set(),get（），remove（）方法的时候，会被亲历掉key为null的记录，使用完ThreadLcoal方法后最好调用remove().





<h5>线程池

池化技术想必大家已经屡见不鲜了，线程池、数据库连接池、Http 连接池等等都是对这个思想的应用。池化技术的思想主要是为了减少每次获取资源的消耗，提高对资源的利用率。

 线程池的好处：

降低资源消耗，提高响应速度，提高线程的可管理性。

实现runable接口和callable接口的区别。

callable可以返回结果或抛出异常。

所以，如果任务不需要返回结果或抛出异常推荐使用 **`Runnable` 接口** ，这样代码看起来会更加简洁。

工具类 `Executors` 可以实现将 `Runnable` 对象转换成 `Callable` 对象。（`Executors.callable(Runnable task)` 或 `Executors.callable(Runnable task, Object result)`）。



执行 execute()方法和 submit()方法的区别是什么呢？

执行execute方法提交不需要返回值的任务，无法判断任务是否被线程池执行执行成功。

submit()方法用于提交需要返回值的任务，线程池会返回一个Future类型的对象，听过这个对象可以判断任务是否执行成功。

如何创建线程池

《阿里巴巴 Java 开发手册》中强制线程池不允许使用 Executors 去创建，而是通过 ThreadPoolExecutor 的方式，这样的处理方式让写的同学更加明确线程池的运行规则，规避资源耗尽的风险。

方式1：通过构造方法。

方式2:executor框架工具类Executors 

我们可以创建三种类型的 ThreadPoolExecutor：

**FixedThreadPool** ： 该方法返回一个固定线程数量的线程池。该线程池中的线程数量始终不变。当有一个新的任务提交时，线程池中若有空闲线程，则立即执行。若没有，则新的任务会被暂存在一个任务队列中，待有线程空闲时，便处理在任务队列中的任务。

**SingleThreadExecutor：** 方法返回一个只有一个线程的线程池。若多余一个任务被提交到该线程池，任务会被保存在一个任务队列中，待线程空闲，按先入先出的顺序执行队列中的任务。

**CachedThreadPool：** 该方法返回一个可根据实际情况调整线程数量的线程池。线程池的线程数量不确定，但若有空闲线程可以复用，则会优先使用可复用的线程。若所有线程均在工作，又有新的任务提交，则会创建新的线程处理任务。所有线程在当前任务执行完毕后，将返回线程池进行复用。

ThreadPoolExecutor三个重要参数:corePoolSize：核心·线程数定义最小可以同时运行的数量。

maximumPoolSize：当对列中存放的任务达到队列的容量的时候，可以同时运行的线程数量变为最大线程数。

workQueue：当新任务来的时候会先判断当前运行的线程数量是否达到了核心线程，如果达到的话，新任务就会被存放在对剋中。

1. **`keepAliveTime`**:当线程池中的线程数量大于 `corePoolSize` 的时候，如果这时没有新的任务提交，核心线程外的线程不会立即销毁，而是会等待，直到等待的时间超过了 `keepAliveTime`才会被回收销毁；
2. **`unit`** : `keepAliveTime` 参数的时间单位。
3. **`threadFactory`** :executor 创建新线程的时候会用到。
4. **`handler`** :饱和策略。关于饱和策略下面单独介绍一下。

ThreadPoolExecutor.AbortPolicy`：** 抛出 `RejectedExecutionException`来拒绝新任务的处理。



<h5>Atomic 原子类 略

AQS略



<h5>堆，方法区

堆和方法区是所有线程共享的资源，堆是用于存放新建的对象，方法区主要用于存放已被加载的类信息，常量，静态变量，即时编译器编译后代码等数据。





<h5>反射

1.获取class对象的四种方式

```java
Class alunbarClass = TargetObject.class;
```

```java
Class alunbarClass1 = Class.forName("cn.javaguide.TargetObject");
```

```java
TargetObject o = new TargetObject();
Class alunbarClass2 = o.getClass();
```

```java
ClassLoader.getSystemClassLoader().loadClass("cn.javaguide.TargetObject");
```



反射的基本操作

```java
package cn.javaguide;

import java.lang.reflect.Field;
import java.lang.reflect.InvocationTargetException;
import java.lang.reflect.Method;

public class Main {
    public static void main(String[] args) throws ClassNotFoundException, NoSuchMethodException, IllegalAccessException, InstantiationException, InvocationTargetException, NoSuchFieldException {
        /**
         * 获取 TargetObject 类的 Class 对象并且创建 TargetObject 类实例
         */
        Class<?> targetClass = Class.forName("cn.javaguide.TargetObject");
        TargetObject targetObject = (TargetObject) targetClass.newInstance();
        /**
         * 获取 TargetObject 类中定义的所有方法
         */
        Method[] methods = targetClass.getDeclaredMethods();
        for (Method method : methods) {
            System.out.println(method.getName());
        }

        /**
         * 获取指定方法并调用
         */
        Method publicMethod = targetClass.getDeclaredMethod("publicMethod",
                String.class);

        publicMethod.invoke(targetObject, "JavaGuide");

        /**
         * 获取指定参数并对参数进行修改
         */
        Field field = targetClass.getDeclaredField("value");
        //为了对类中的参数进行修改我们取消安全检查
        field.setAccessible(true);
        field.set(targetObject, "JavaGuide");

        /**
         * 调用 private 方法
         */
        Method privateMethod = targetClass.getDeclaredMethod("privateMethod");
        //为了调用private方法我们取消安全检查
        privateMethod.setAccessible(true);
        privateMethod.invoke(targetObject);
    }
}


```

