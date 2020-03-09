# C-
my study notes
单纯的用来做一个C#学习的笔记，不要问我为啥变成C-了，我也不知道。
### Solution 解决方案 一个solution里面可以有多个project。
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
*必须是形参列表中的最后一个，由params修饰*，eg String.Format String.Split方法。
## 具名参数
大概就是 创建一个方法 static void eg{string name, int age} {Console.WriteLine("Hello{0} you are {1}");},然后再另一个方法里面调用 eg(age:15, name:"Moe_Nya");
## 可选参数
参数具有默认值而变得“可选”。比如参数在声明的时候就给它默认值：static void eg{string name = "Moe_Nya", int age = 15} {Console.WriteLine("Hello{0} you are {1}");}
## 扩展方法（this）注意“this”的使用
顾名思义自己弄一个方法出来，具体操作如下 public static double Round(this double put，int out) {double result = Math.Round(put, put); return result} 在另一个方法中 来简化小数位数 double x = 3.1415926; double y = x.Round(4); *这里的x.Round如果没有上面的this的话是不存在的，就是说这里的Round是自己创造的* 。*扩展方法必须是公有，静态的，必须被 public static所修饰，同时必须是形参列表中的最后一个。*
### LINQ方法
eg 
```
class Program
{
    static void Main(string[] args)
    {
        var myList = new List<int>(){ 11, 12, 9, 14, 15 };
        //bool result = AllGreaterThanTen(myList);
        // 这里的 All 就是一个扩展方法
        bool result = myList.All(i => i > 10);
        Console.WriteLine(result);
    }

    static bool AllGreaterThanTen(List<int> intList)
    {
        foreach (var item in intList)
        {
            if (item <= 10)
            {
                return false;
            }
        }

        return true;
    }
}
```
#### 传值参数：参数的默认传递方式<br>输出参数：用于除返回值以外还需要输出的场景<br>引用参数：用与需要修改实际参数的场景<br>数组参数：用于简化方法的调用<br>具名参数：提高可读性<br>可选参数：参数具有默认值<br>扩展方法（this参数）：为目标数据类型追加方法
## 委托
### 什么是委托
#### C#中的委托就相当于指针的升级版
#### 一切皆地址
##### 变量（数据）是以某个地址为起点的一段内存中所储存的值。
##### 函数（算法）是以某个地址为起点的一段内存中所储存的一组机器语言指令。
#### 直接调用与间接调用
##### 直接调用：通过函数名来调用函数，CPU通过函数名直接获得函数所在地址并开始执行并返回。
##### 间接调用：通过函数指针来调用函数，CPU通过读取函数指针储存的值获得函数所在地址并开始执行并返回。
#### JAVA中没有与委托相对应的功能实体。
#### 委托的简单使用
##### Action 委托
```
class Program
{
    static void Main()
    {
        Eg eg = new Eg();创建实例
        Action action = new action(eg.Eg1);//拿到方法名
        eg.Eg();//直接调用
        Action.Invoke();//间接调用
        Action();//简便方法
    }
}
class Eg
{
    public void Eg1()
    {
        Console.WriteLine("ddd");
    }
    public int Add(int a, int b)
    {
        a + b;
    }
}
```
##### Func 委托
```
Func<int, int, int>func1 = new Func<int, int, int>(eg.Add)
int x = 100; int y = 200; int z = 0;
z = func1.Invoke<x, y>
Console.WriteLine(z);
```
### 委托的声明（自定义委托）
#### 委托是一种类，类是一种数据类型，所以委托也是一种数据类型。
#### 它的声明方式与一般的类不同，主要是为了照顾可读性和C/C++传统。
#### 注意声明委托的位置
##### 避免写错地方结果写成嵌套类型。
```
public delegate 目标方法的返回值类型 委托类型(根据目标方法声明参数);
```
然后后面的操作就和上面一样了。
#### 委托与封装的方法必须“类型兼容”。
### 委托的使用
正确使用1：“模板方法”，“借用”借用指定的外部方法来产生结果。<br>
正确使用2：“回调方法（callback）”，调用指定的外部方法。<br>
缺点：1.这是一种方法级别的紧耦合，现实工作中慎之又慎。2.把委托回调，异步调用和多线程纠缠在一起，让代码变得难以阅读和维护。3.委托使用不当可能导致内存泄漏和程序性能下降。
### 委托的高级使用
1.多播（multicast）委托：一个委托里面还有多个委托。<br>
```
using System;
using System.Threading;

namespace DelegateExample
{
    class Program
    {
        static void Main(string[] args)
        {
            var stu1 = new Student { ID = 1, PenColor = ConsoleColor.Yellow };
            var stu2 = new Student { ID = 2, PenColor = ConsoleColor.Green };
            var stu3 = new Student { ID = 3, PenColor = ConsoleColor.Red };
            var action1 = new Action(stu1.DoHomework);
            var action2 = new Action(stu2.DoHomework);
            var action3 = new Action(stu3.DoHomework);

            // 单播委托
            //action1.Invoke();
            //action2.Invoke();
            //action3.Invoke();

            // 多播委托
            action1 += action2;
            action1 += action3;

            action1.Invoke();
        }
    }

    class Student
    {
        public int ID { get; set; }
        public ConsoleColor PenColor { get; set; }

        public void DoHomework()
        {
            for (int i = 0; i < 5; i++)
            {
                Console.ForegroundColor = PenColor;
                Console.WriteLine("Student {0} doing homework {1} hour(s)", ID, i);
                Thread.Sleep(1000);
            }
        }
    }
}
```
2.隐式异步调用（注意“同步”和“异步”的中英文意思的差距）<br>
3.应该适时的地使用接口（interface）取代一些对委托的使用。
## 事件详解1
定义：Event，“能够发生的事情”<br>
角色：使对象或类具备通知能力的成员<br>
使用：用于对象或类间的动作协调与信息传递（消息推送）<br>
事件的功能 = 通知 + 可选的事件参数（即详细信息）
## 事件详解2
事件模型的5个组成部分：1.事件的拥有者（event source 对象） 2.事件成员（event 成员） 3.事件的响应者（event subscriber 对象） 4.事件的处理器（event handler 成员）--本质上是一个回调方法 5.事件订阅--把事件处理器和事件关联在一起，本质上是一种以委托类型为基础的“约定”。<br>
事件不会“发声”，一定是被拥有者的某些内部逻辑所触发才会“发声”。<br>
事件订阅的操作符是“+=”，左边是事件，右边是事件处理器。
## 事件的声明方式
### 事件完整声明方式
```
using System;
using System.Threading;

namespace EventExample
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1.事件拥有者
            var customer=new Customer();
            // 2.事件响应者
            var waiter=new Waiter();
            // 3.Order 事件成员 5. +=事件订阅
            customer.Order += waiter.Action;

            customer.Action();
            customer.PayTheBill();
        }
    }

    // 该类用于传递点的是什么菜，作为事件参数，需要以 EventArgs 结尾，且继承 EventArgs
    public class OrderEventArgs:EventArgs
    {
        public string DishName { get; set; }

        public string Size { get; set; }
    }

    // 声明一个委托类型，因为该委托用于事件处理，所以以 EventHandler 结尾
    // 注意委托类型的声明和类声明是平级的
    public delegate void OrderEventHandler(Customer customer, OrderEventArgs e);

    public class Customer
    {
        // 委托类型字段
        private OrderEventHandler orderEventHandler;

        // 事件声明
        public event OrderEventHandler Order
        {
            add { this.orderEventHandler += value; }
            remove { this.orderEventHandler -= value; }
        }

        public double Bill { get; set; }

        public void PayTheBill()
        {
            Console.WriteLine("I will pay ${0}.",this.Bill);
        }

        public void WalkIn()
        {
            Console.WriteLine("Walk into the restaurant");
        }

        public void SitDown()
        {
            Console.WriteLine("Sit down.");
        }

        public void Think()
        {
            for (int i = 0; i < 5; i++)
            {
                Console.WriteLine("Let me think ...");
                Thread.Sleep(1000);
            }

            if (this.orderEventHandler != null)
            {
                var e=new OrderEventArgs();
                e.DishName = "Kongpao Chicken";
                e.Size = "large";

                this.orderEventHandler.Invoke(this,e);
            }
        }

        public void Action()
        {
            Console.ReadLine();
            this.WalkIn();
            this.SitDown();
            this.Think();
        }
    }

    public class Waiter
    {
        // 4.事件处理器
        public void Action(Customer customer, OrderEventArgs e)
        {
            Console.WriteLine("I will serve you the dish - {0}.",e.DishName);

            double price = 10;
            switch (e.Size)
            {
                case "small":
                    price *= 0.5;
                    break;
                case "large":
                    price *= 1.5;
                    break;
                default:
                    break;
            }
            customer.Bill += price;
        }
    }
}
```
### 事件简略声明方式
```
using System;
using System.Threading;

namespace EventExample
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1.事件拥有者
            var customer=new Customer();
            // 2.事件响应者
            var waiter=new Waiter();
            // 3.Order 事件成员 5. +=事件订阅
            customer.Order += waiter.Action;

            customer.Action();
            customer.PayTheBill();
        }
    }

    public class OrderEventArgs:EventArgs
    {
        public string DishName { get; set; }

        public string Size { get; set; }
    }

    public delegate void OrderEventHandler(Customer customer, OrderEventArgs e);

    public class Customer
    {
        // 简略事件声明，看上去像一个委托（delegate）类型字段
        public event OrderEventHandler Order;

        public double Bill { get; set; }

        public void PayTheBill()
        {
            Console.WriteLine("I will pay ${0}.",this.Bill);
        }

        public void WalkIn()
        {
            Console.WriteLine("Walk into the restaurant");
        }

        public void SitDown()
        {
            Console.WriteLine("Sit down.");
        }

        public void Think()
        {
            for (int i = 0; i < 5; i++)
            {
                Console.WriteLine("Let me think ...");
                Thread.Sleep(1000);
            }

            if (this.Order != null)
            {
                var e=new OrderEventArgs();
                e.DishName = "Kongpao Chicken";
                e.Size = "large";

                this.Order.Invoke(this,e);
            }
        }

        public void Action()
        {
            Console.ReadLine();
            this.WalkIn();
            this.SitDown();
            this.Think();
        }
    }

    public class Waiter
    {
        // 4.事件处理器
        public void Action(Customer customer, OrderEventArgs e)
        {
            Console.WriteLine("I will serve you the dish - {0}.",e.DishName);

            double price = 10;
            switch (e.Size)
            {
                case "small":
                    price *= 0.5;
                    break;
                case "large":
                    price *= 1.5;
                    break;
                default:
                    break;
            }
            customer.Bill += price;
        }
    }
}
```
### 事件的本质是委托字段的一个包装器，这个包装器对委托字段的访问起限制作用。