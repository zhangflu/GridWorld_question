vi
==

vi的状态 
-----
基本上 vi 可以分为三种状态，分别是命令模式（command mode）、插入模式（Insert mode）
和底行模式（last line mode），各模式的功能区分如下：

 - 命令行模式 command mode）
控制屏幕光标的移动，字符、字或行的删除，移动复制某区段及进入 Insert mode 下，
或者到 last line mode。
 - 插入模式（Insert mode）
只有在 Insert mode 下，才可以做文字输入，按「ESC」键可回到命令行模式。
 - 底行模式（last line mode）

在「命令行模式（command mode）」下按一下字母「i」就可以进入「插入模式（Insert
mode）」，这时候你就可以开始输入文字了。 

如果您发现输错了字！
想用光标键往回移动，将该字删除，就要先按一下「ESC」键转到「命令行模式（command
mode）」 再删除文字。 

在「命令行模式（command mode）」下，按一下「：」冒号键进入「Last line mode」，例
如：

 - :w filename （输入 「w filename」将文章以指定的文件名 filename 保存）
 - :wq (输入「wq」，存盘并退出 vi)
 - :q! (输入 q!， 不存盘强制退出 vi) 

常用命令：
-----

 - 删除文字
「x」：每按一次，删除光标所在位置的“后面”一个字符。
「#x」：例如，「6x」表示删除光标所在位置的“后面” 6 个字符。
「X」：大写的 X，每按一次，删除光标所在位置的“前面”一个字符。
「#X」：例如，「20X」表示删除光标所在位置的“前面” 20 个字符。
「dd」：删除光标所在行。
「#dd」：从光标所在行开始删除#行
 - 复制
「yw」：将光标所在之处到字尾的字符复制到缓冲区中。
「#yw」：复制#个字到缓冲区
「yy」：复制光标所在行到缓冲区。
「#yy」：例如，「6yy」表示拷贝从光标所在的该行“往下数” 6 行文字。
「p」：将缓冲区内的字符贴到光标所在位置。注意：所有与“y”有关的复制命令都必
须与“p”配合才能完成复制与粘贴功能。 

 - 跳至指定的行
「ctrl」 +「g」列出光标所在行的行号。
「#G」：例如，「15G」，表示移动光标至文章的第 15 行行首。 

 - 查找字符
「/关键字」：先按「/」键，再输入您想寻找的字符，如果第一次找的关键字不是您想要
的，可以一直按「n」会往后寻找到您要的关键字为止。 

 - 复制
要选中内容进行复制，先在命令模式下按 v 进入 Visual Mode，然后用 方向键 或 hjkl 选择文本，再按 y 进行复制，再按 d 进行剪切。p    粘贴至游标后

 - 撤销
在命令行模式下用 :undo 或 :u 命令可以撤销最近一次操作

JAVA
==

引用
-----
引用类型变量在声明后必须通过实例化开辟数据
空间，才能对变量所指向的对象进行访问。 
`MyDate today； //将变量分配一个保存引用的空间
today = new MyDate（）； //这句话是 2 步，首先执行 new MyDate（），给today 变量开辟数据空间，然后再执行赋值操作。 `
装箱和拆箱
-----
我们现在知道了，所有对象型的数据类型的基类是java.lang.Object .而写java
程序的时候非常多的工作都是在写这些类，和实现里面的方法。而偏偏就有那么
8 种基本类型和他们不一样。以至于让你来回在这两种之间转换，这是很让人头疼的事情。 Java中int， long， char这样的类型不是对象型。因此java里提供了一种
叫做包装类（wrapper）的东西，使基本类型，有着相应的对象类型Integer， Long，Character等。这样就可以，先把基本类型的东西，转成对象来用，然后再转回去。 
对象
-----
在 java 语言中，数组就是一个对象，所以创建数组与创建对象一样也
是用 new 关键字来创建。举个例子， s = new char[20]; p = new Point[50]。 

在 jdk5.0 中，我们发现了一些更简单的方法，打印一维数组时，用
toString(array)方法，打印二维数组时，用 deepToString(array)方法。这样的话就
剩了我们又是循环又是判断的。 
集合
-----
Set 的子接口有 TreeSet，SortedSet，List 的有 ArrayList 等，Map 里有 HashMap，HashTable等， Queue 里面有 BlockingQueue 等 
继承
-----
这样的将子类型的对象引用转换成父类型的对象引用，叫做上溯造型
（upcasting）。
我们再来引伸一下，我们在数组那节课里讲了，数组存放的元素是相同类型
的数据，但是上溯造型使得 java 允许创建不同类型对象的数组。
Object 型的话 Object[] obj=new Object[]；那就是里面放什么对象都行了。因为什么对象都可以是 Object 型的 
垃圾收集器
-----
可是垃圾收集器却以较低的优先级在系统空闲周期中执行，通俗一点说就是
它级别低，别人不运行时候才轮到它，因此垃圾收集器的速度比较慢。有些时候我们会使用 System.gc（）。手动回收。这样来提高性能。
对于垃圾收集器来说还有一个值得一提的是 finalize（）这个方法，每一个对象都有一个finalize（）方法，这个方法是从 Object 类继承来的。它用来回收内存以外的系统资源，就像是文件处理器和网络连接器。该方法的调用顺序和用来调用该方法的对象的创建顺序是无关的。换句话说，书写程序时该方法的顺序和方法的实际调用顺序是不相干的。这只是finalize（）方法的特点。还有，每个对象只能调用 finalize（）方法一次。如果在 finalize（）方法执行时产生异
常（exception），则该对象仍可以被垃圾收集器收集。那是一定了，不能说用到finalize（）了。垃圾收集器就什么也不做了啊。finalize（）的工作量是很大的哦 

根据垃圾收集器的工作原理，我们可以通过一些技巧和方式，让垃圾收集器

 - 最基本的建议就是尽早释放无用对象的引用。
大多数程序员在使用临时变量的时候，都是让引用变量在退出活动域
（scope）后，自动设置为 null.
 - 尽量少用finalize函数。 finalize函数是Java提供给程序员一个释放对象或资
源的机会。但是，它会加大垃圾收集器的工作量，因此尽量少采用finalize方式回
收资源。
 - 当程序有一定的等待时间，程序员可以手动执行 System.gc（），通知垃圾收集器运行，但是 Java 语言规范并不保证垃圾收集器一定会执行 


**注意：子类不能重写父类的静态方法，也不能把父类不是静态的重写成静态的方法。想隐藏父类的静态方法的话，在子类中声明和父类相同的方法就行了** 
static代码块
-----
static代码块也叫静态代码块，是在类中独立于类成员的static语句块，可以有多个，位置可以随便放，它不在任何的方法体内，JVM加载类时会执行这些静态的代码块，如果static代码块有多个，JVM将按照它们在类中出现的先后顺序依次执行它们，每个代码块只会被执行一次。
利用静态代码块可以对一些static变量进行赋值

> 来自 <https://zhidao.baidu.com/question/475807775.html>
抽象与接口
-----
Java语言中允许有一种叫做抽象方法的东西，他只是一个名字没有具体的实现。
像是这样：`public abstract void abc（）；`
使用了abstract关键字，结尾用“； ”结束。 
 
概念：包含一个或多个抽象方法的类
称为抽象类。抽象类也必须声明abstract关键字。抽象类的使用有着一些限制，不能创建抽象类的实例。如果子类实现了抽象方法，则可以创建该子类的实例对象。要是子类也不实现的话，这个子类也是抽象类，也不能创建实例。
 
接口是什么东西呢？接口是比抽象类更抽象的类。举例： public interface
Name { }接口里面的方法全都是抽象的，里面的变量全都是 final 的常量，而且
实现接口的类必须将所有的抽象方法全部实现。抽象类里也可以有具体的方法。
所以说，接口是最抽象的，其次是抽象类，而具体类本身就是对现实世界的抽象。
软件开发本身就是将现实世界抽象成计算机世界。 

接口的实现用关键字 implement 而不是 extends.如果用了 extends 的那就是
继承这个接口。那么那个子类也是接口，是原来的子接口。 
异常处理
-----
ArrayIndexOutOfBoundsException（数组边界溢出），
NullPointerException（空指针异常）。 
I/O
-----
java 语言中， I/O 的方式是流的方式。流（stream）这是个学习 java 输入输出的最基本的概念。流是字节从源到目的的有序序列。
一方面是字节，一方面是有序的。流描述的是一个过程，顺序严格。 
这些东西都放在 java.io.*这个包里了。 

 - 从命令行输入输出数据
1.向控制台输出数据
标准输出流（System.out）中为人们提供了3种输出方法：
1）print(输出项)：实现不换行输出。输出项可以是变量名、常量、表达式。
2）println（输出项）：输出数据后换行。输出项可以是变量名、常量、表达式。
3）printf（"格式控制部分”,表达式1,表达式2，....表达式n）：格式控制部分由“格式控制符”+“普通字符组成”。。。普通字符原样输出；常用的格式控制符有：
      %d（代表十进制数）、%c（代表一个字符）、%f（代表浮点数）、%e（代表科学计数法的浮点数）、%s（代表字符串）、%n（代表换行符）。。。。
      输出时也可以控制数据的宽度：
      %md：输出的int型数组占m列            %m.nf：输出的浮点型数组占m列，小数点部分保留n位             %.nf：

 - 从控制台输入数据
1.使用Scanner类---------java.util.Scanner类 。 步骤：
    ---------------------------     import java.util.*;
    ---------------------------     构造Scanner类对象，它附属于标准输入流System.in                 如：Scanner sb = new Scanner(System.in);
    ---------------------------     常用的next()方法系列：       nextInt():输入整数    nextLine():输入字符串     nextDouble():输入双精度数     next():输入字符串（以空格作为分隔符）
举例：

```
import java.util.*;  
public class DEMO_1 {  
     public static void main(String[] args){  
        Scanner sb = new Scanner(System.in);  
        System.out.print("输入你的姓名：");  
        String name = sb.nextLine();  
        System.out.print("输入你的年龄：");  
        int age = sb.nextInt();  
        System.out.println("姓名：" + name + "  年龄：" + age );  
        sb.close();         //若没有关闭Scanner对象将会出现警告  
     }  
}
```

运行： 

	1. 输入你的姓名：一吨重的肥羊  
	2. 输入你的年龄：99  
	3. 姓名：一吨重的肥羊  年龄：99  

> 来自 <https://blog.csdn.net/qq_33218411/article/details/68947559>

多线程 
-----
在 java 中如何写线程呢，在 java 中就是很简单了。有两种方法：第一、继
承 java.lang.Thread 第二、实现 Runnable 接口。 


Ant
==

关键元素
-----
Ant的构件文件都是XML格式的。每个构件文件包含一个project元素和至少一个target。
target元素可以包含多个task元素。 

 - Project 元素
project 元素是构建文件的根元素。 
一个 project 元素可以有多个 target 元素，一个 target 元素可以有多个 task。
project标签里有三个属性: 


    `<project name="MyProject" default="dist" basedir=".">`

    name属性，指示 project 元素的名字。例子中的名字就是 MyProject。
default属性，指示这个 project 默认执行的 target。在本文的例子中，默认执行的 target 为 dist。如果我们输入命令 ant 时，不指定 target 参数，默认会执行 dist 这个 target。
basedir属性，指定根路径的位置。该属性没有指定时，使用Ant的构件文件的所在目录作为根目录。
 - Target 元素
target 元素是 task 的容器，也就是 Ant 的一个基本执行单元。 
以上节例子中的 compile 来举例。
`<target name="compile" depends="init" description="compile the source " >
    <!-- Compile the java code from srcinto
{build} -->
    <javac srcdir="${src}" destdir="${build}"/>
</target>`
这个 target 中出现了几个属性。
 - name属性，指示target元素的名称。
这个属性在一个project元素中必须是唯一的。这很好理解，如果出现重复，Ant就不知道具体该执行哪个 target 了。
 - depends属性，指示依赖的 target，当前的 target 必须在依赖的 target 之后执行。
 - description属性，是关于 target 的简短说明。
此外，还有其他几个未出现在构建文件中的属性。
 - if属性，验证指定的属性是否存在，若不存在，所在target将不会被执行。
 - unless属性，正好和 if属性相反，验证指定的属性是否存在，若存在，所在target将不会被执行。
extensionOf属性，添加当前 target 到 extension-point 依赖列表。
 - Ant1.8.0新特性
	extension-point 元素和 target 元素十分类似，都可以指定依赖的target。但是不同的是，extension-point 中不能包含任何 task。
请看以下实例： 
`<target name="create-directory-layout">
   ...
</target>
<extension-point name="ready-to-compile" depends="create-directory-layout"/>
<target name="compile" depends="ready-to-compile">
   ...
</target>`
*调用target顺序:  create-directory-layout --> 'empty slot' --> compile* 
`<target name="generate-sources" extensionOf="ready-to-compile">
   ...
</target>`
*调用target顺序:  create-directory-layout --> generate-sources  --> compile*
 - onMissingExtensionPoint属性：当无法找到一个extension-point时，target尝试去做的动作("fail", "warn", "ignore")。——Ant1.8.2新特性。
 - Task 元素
task是一段可以被执行的代码。
一个task可以有多个属性， 一个属性可以包含对一个 property 的引用。
task的通常结构为
<name attribute1="value1" attribute2="value2" ... />
其中，name 是 task 的名字， attributeN 是属性名， valueN 是这个属性的值。
还是以 compile 做为例子：
`<target name="compile" depends="init" description="compile the source " >
    <!-- Compile the java code from srcinto
{build} -->
    <javac srcdir="${src}" destdir="${build}"/>
</target>`
在 compile 这个 target 标签中包含了一个任务。
这个任务的动作是：执行JAVA编译，编译src下的代码，并把编译生成的文件放在build目录中。
常用task
-----
 - javac：用于编译一个或者多个Java源文件，通常需要srcdir和destdir两个属性，用于指定Java源文件的位置和编译后class文件的保存位置。
`<javac srcdir="${src}" destdir="${build}" classpath="abc.jar" debug="on" source="1.7" />`
 - java：用于运行某个Java类，通常需要classname属性，用于指定需要运行哪个类。
`<java classname="test.Main">
    <arg value="-h" />
    <classpath>
        <pathelement location="dist/test.jar" />
    </classpath>
</java>`
 - jar：用于生成JAR包，通常需要指定destfile属性，用于指定所创建JAR包的文件名。除此之外，通常还应指定一个文件集，表明需要将哪些文件打包到JAR包里。
`<jar jarfile="dist/lib/MyProject−
{DSTAMP}.jar" basedir="${build}"/>`

 - echo：输出某个字符串
`<echo message="Building to ${builddir}"/>
<echo>You are using version ${java.version} of Java! This message spans two lines.</echo>`
 - copy：用于复制文件或路径。
`<copy todir="${builddir}/srccopy">
    <fileset dir="${srcdir}">
        <include name="**/*.java"/>
    </fileset>
    <filterset>
        <filter token="VERSION" value="${app.version}"/>
    </filterset>
</copy>`

 - delete：用于删除文件或路径。
`<delete file="/lib/ant.jar" />
<delete dir="lib" />
<delete>
    <fileset dir="." includes="**/*.bak" />
</delete>`
 - mkdir：用于创建文件夹。
`<mkdir dir="${dist}/lib" />`
 - move：用户移动文件和路径。
`<move todir="some/new/dir">
    <fileset dir="my/src/dir">
        <include name="**/*.jar" />
        <exclude name="**/ant.jar" />
    </fileset>
</move>`

 - Property 元素
Property 是对参数的定义。
project的属性可以通过property元素来设定，也可在Ant之外设定。若要在外部引入某文件，例如build.properties文件，可以通过如下内容将其引入：
`<property file=” build.properties”/>`
property元素可用作 task 的属性值。在task中是通过将属性名放在`“${”和“}”`之间，并放在task属性值的位置来实现的。
例如 complile 例子中，使用了前面定义的 src 作为源目录。 
<javac srcdir="${src}" destdir="${build}"/>
Ant提供了一些内置的属性，它能得到的系统属性的列表与Java文档中System.getPropertis()方法得到的属性一致，这些系统属性可参考sun网站的说明。
 
 - extension-point元素
和 target 元素十分类似，都可以指定依赖的target。但是不同的是，extension-point 中不能包含任何 task。——Ant1.8.0新增特性。
在 target元素中的例子里已提到过，不再赘述。 
  

> 参考资料 [1] ant官方手册：http://ant.apache.org/manual/index.html  [2]
> http://www.blogjava.net/amigoxie/archive/2007/11/09/159413.html
> 
> 来自 <https://www.cnblogs.com/jingmoxukong/p/4433945.html> 
> 
> ant使用指南详细入门教程
> 
> 来自 <http://www.jb51.net/article/67041.htm>

Junit
==

Annotation 注释
-----
元数据:

 - @Before：
使用了该元数据的方法在每个测试方法执行之前都要执行一次。 
 - @After：
使用了该元数据的方法在每个测试方法执行之后要执行一次。
注意： @Before 和@After 标示的方法只能各有一个。这个相当于取代了 JUnit 以前版本中的
setUp 和 tearDown 方法，当然你还可以继续叫这个名字，不过 JUnit 不会霸道的要求你这么
做了。
 - @Test(expected=*.class)
在 JUnit4.0 之前，对错误的测试，我们只能通过 fail来产生一个错误，并在 try 块里面 assertTrue
（true）来测试。现在，通过@Test 元数据中的 expected 属性。 expected 属性的值是一个异
常的类型
 - @Test(timeout=xxx):
该元数据传入了一个时间（毫秒）给测试方法，
如果测试方法在制定的时间之内没有运行完，则测试也失败。
 - @ignore：
该元数据标记的测试方法在测试中会被忽略。当测试的方法还没有实现，或者测试的方法已
经过时，或者在某种条件下才能测试该方法（比如需要一个数据库联接，而在本地测试的时
候，数据库并没有连接），那么使用该标签来标示这个方法。同时，你可以为该标签传递一
个 String 的参数，来表明为什么会忽略这个测试方法。比如： @lgnore(―该方法还没有实现‖)，
在执行的时候，仅会报告该方法没有实现，而不会运行测试方法。 

为了验证环境是否配置正确，我们编写一个类，和一个测试类。

    ----HelloWorld.java------
    import java.util.*;
    public class HelloWorld {
    String str;
    Public void hello()
    {
        str = ―Hello World!‖;
    } 
    Public String getStr()
    {
        Return str;
        }
    }
    -----HelloWorldTest.java----------
    import static org.junit.Assert.*;
    import org.junit.Test;
    public class HelloWorldTest {
    public HelloWorld helloworld = new HelloWorld();
    @Test
    Public void testHello() {
        helloworld.hello();
        assertEquals(―Hello World!‖, helloworld.getStr());
        }
    }

把这两个文件放在同一个目录下。
使用如下命令运行：

    @sser>javac –classpath .:junit-4.9.jar HelloWorldTest.java
    @sser>java –classpath .:junit-4.9.jar –ea org.junit.runner.JUnitCore HelloWorldTest

可得到如下输出结果：

    JUnit version 4.9
    .
    Time 0.007
    OK(1 test)

我们可以看到运行正确，这也证明了我们的环境配置正确。