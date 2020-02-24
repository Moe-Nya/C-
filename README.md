# C-
my study notes
单纯的用来做一个C#学习的笔记，不要问我为啥变成C-了，我也不知道。
Solution 解决方案 一个solution里面可以有多个project。
# 类 class 
类 构成程序的主体 名称空间 namespace 将类组织在一起
C#是完全面向对象的，所有程序都要包括进类。
using 用于引用名称空间，（引用微软已经做好的类）相当于C语言的#include。
类和名称空间都放在类库中，类库是使用名称空间的物理基础。
类的3大成员：1.属性（Property）2.方法（Method）3.事件（Event）
# 数据类型
数据类型有1.值类型 2.引用类型 3.指针类型 具体的上网搜。
类型转换：比如 double x = 5.12; int i; i = int(x);这个就是将x转换为int类型，然后赋给i，虽然不知道这样写可以干啥，反正是这样操作的就完事了。
其他的转换方式也是同理：int i = 100; Console.WriteLine(i ToChar());
# 什么是类型？
数据在内存中储存时的“型号”  C#中的五大数据类型：1.类（classes） 2.结构体（structures） 3.枚举（enumerations） 4.接口（interface） 5.委托（delegates）
使用 new 操作符创建类的实例。比如 Form myForm = new Form;
# 练习
花了一些时间跟着写了了两个网上的项目，一个是一个C#做的音乐播放器，效果还行~ 第二个是一个.NET 做的百度图片爬虫，最后做是做出来的，爬取的的效果不怎么样，因为我不会.NET所以也不能做什么优化，就当作完成啦。写过一些代码过后就去安装了Unity，然后也是学着做了一个2D横板的demo，也只是知道了怎么做人物的移动，其他的东西也就了解了一下。做完了这些于是我又回来继续学C#啦，值得注意的是，在切切实实的写过C#过后再回来学习基础，会发现自己理解领悟的比啥都不知道一上来直接学基础的要快。
# 变量
一共有7种，静态变量，实例变量（成员变量，字段），数组变量，值参数，引用参数，输出形参，局部变量。
变量是以变量名所对应的内存地址为起点，以其数据类型所要求的储存空间为长度的一块内存区域。
# Debug的方法
## 设置断点
程序运行到断点处会暂停
## 观察方法调用时的call stack
程序调试的时候在vs的下面显示出 可以查看调用关系
## Step-into Step-over Step-out
Step-into遇到子函数就继续单步入执行。Step-over不会进入子函数，而是把子函数执行完再停下来。Step-out当单步执行到子函数时，可以执行完子函数余下的部分，并且返回上一函数。
## 观察局部变量的值与变化
# 操作符
https://www.runoob.com/csharp/csharp-operators.html
# 传值参数和引用参数和输出形参
值参数是方法之外变量的副本，对副本的操作不会影响到方法外部的变量。而引用参数不会对传进来的值建副本，引用参数指向的地址就是实际参数的地址。
所以传值参数引用时变量和参数指向同一个内存地址，引用参数引用时是参数指向变量再指向内存地址。
## 数组参数
必须是形参列表中的最后一个，由params修饰，eg String.Format String.Split方法。
## 具名参数
大概就是 创建一个方法 static void eg{string name, int age} {Console.WriteLine("Hello{0} you are {1}");},然后再另一个方法里面调用 eg(age:15, name:"Moe_Nya");
## 可选参数
参数具有默认值而变得“可选”。比如参数在声明的时候就给它默认值：static void eg{string name = "Moe_Nya", int age = 15} {Console.WriteLine("Hello{0} you are {1}");}
## 扩展方法（this）注意“this”的使用
顾名思义自己弄一个方法出来，具体操作如下 public static double Round(this double put，int out) {double result = Math.Round(put, put); return result} 在另一个方法中 来简化小数位数 double x = 3.1415926; double y = x.Round(4); *这里的x.Round如果没有上面的this的话是不存在的，就是说这里的Round是自己创造的* 。