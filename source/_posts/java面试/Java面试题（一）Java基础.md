---
title: Java面试题汇总（一）Java基础
date: 2019-03-13 11:43:51
tags:
- java
- 面试题
- 面试
---

## [Java面试题汇总](/2019/03/13/java面试/Java面试题汇总/)（一）Java基础

#### JDK和JRE有什么区别？

- JDK：Java Development Kit 的简称，java 开发工具包，提供了 java 的开发环境和运行环境。
- JRE：Java Runtime Environment 的简称，java 运行环境，为 java 的运行提供了所需环境。

其实JDK包含了JRE，同时还包含了编辑java源码的编译器javac，还包含了很多java程序调试和分析的工具，简单来说：如果你需要运行java程序，只需要安装JRE就可以了，如果你还需要编写java程序，需要安装JDK。

#### == 和 equals 的区别是什么？

==对于基本类型比较的是值，对于引用类型比较的是引用（内存地址）。

equals是Object类的一个方法，它里面返回的就是==的判断，由于所有的类都是继承自java.lang.Object类的，所以适用于所有对象，如果没有对该方法进行覆盖的话，那它就是比较的内存地址。但是实际应用中，我们往往重写equals方法，来比较两个对象的内容是否相等，比如我们常用的String，Integer等类，它们就重写了equals方法，比较的是对象里的内容。

**java.lang.Object类里的equals方法：**

```java
    public boolean equals(Object obj) {
        return (this == obj);
    }
```

**java.lang.String类里的equals方法：**

```java
    public boolean equals(Object anObject) {
        if (this == anObject) {
            return true;
        }
        if (anObject instanceof String) {
            String anotherString = (String)anObject;
            int n = value.length;
            if (n == anotherString.value.length) {
                char v1[] = value;
                char v2[] = anotherString.value;
                int i = 0;
                while (n-- != 0) {
                    if (v1[i] != v2[i])
                        return false;
                    i++;
                }
                return true;
            }
        }
        return false;
    }
```

**总结** ：== 对于基本类型来说是值比较，对于引用类型来说是比较的是引用；而 equals 默认情况下是引用比较，只是很多类重写了 equals 方法，比如 String、Integer 等把它变成了值比较，所以一般情况下 equals 比较的是值是否相等。

#### 两个对象的 hashCode()相同，则 equals()也一定为 true，对吗？

错，两个对象的 hashCode()相同， equals()不一定为 true。

——》单独文章说明。

#### final 在 java 中有什么作用？

- final 修饰的类叫最终类，该类不能被继承；
- final 修饰的方法不能被重写，但是可以被重载；
- final 修饰的变量叫常量，常量使用时必须被初始化， 初始化之后就不能被修改。final修饰的变量一些情况下可以先声明后赋值：1.类里面的成员变量可以先声明，在代码块或者构造函数里面赋值，有多个构造函数时，每个构造函数里都需要赋值。2.方法里的变量可以先声明，使用时必须先赋值。

#### java 中的 Math.round(-1.5) 等于多少？

等于 -1，因为在数轴上取值时，中间值（0.5）向右取整，所以正 0.5 是往上取整，负 0.5 是直接舍弃。

round() 方法返回一个最接近的 int、long 型值，四舍五入。算法为**Math.floor(x+0.5)** ，即将原来的数字加上 0.5 后再向下取整，所以 Math.round(11.5) 的结果为 12，Math.round(-11.5) 的结果为 -11，语法格式：

```java
long round(double d)
    
int round(float f)
```

#### String 属于基础的数据类型吗？

String是引用类型，不属于基础的数据类型。基础数据类型有8种：byte，short，int，long，float，double，char，boolean。

#### java 中操作字符串都有哪些类？它们之间有什么区别？

操作字符串的类有：String、StringBuffer、StringBuilder。

String 和 StringBuffer、StringBuilder 的区别在于 String 声明的是不可变的对象，每次操作都会生成新的 String 对象，然后将指针指向新的 String 对象，而 StringBuffer、StringBuilder 可以在原有对象的基础上进行操作，所以在经常改变字符串内容的情况下最好不要使用 String。

StringBuffer 和 StringBuilder 最大的区别在于，StringBuffer 是线程安全的，而 StringBuilder 是非线程安全的，但 StringBuilder 的性能却高于 StringBuffer，所以在单线程环境下推荐使用 StringBuilder，多线程环境下推荐使用 StringBuffer。

#### String str="i"与 String str=new String("i")一样吗？

不一样，因为内存的分配方式不一样。String str="i"的方式，java虚拟机会将其分配到常量池中；而String str=new String("i")则会被分配到堆内存中。

#### 如何将字符串反转？

使用 StringBuilder 或者 StringBuffer 类的 reverse() 方法。

#### String 类的常用方法都有那些？

- indexOf()：返回指定字符的索引；
- charAt()：返回指定索引处的字符；
- split()：根据指定字符串进行分割字符串，返回一个String数组；
- substring()：截取字符串；
- replace()：字符串替换；
- equals()：字符串比较；
- trim()：去除字符串两端空白；
- getBytes()：返回字符串的byte类型数据；
- length()：返回字符串的长度；
- toLowerCase()：将字符串转为小写字母；
- toUpperCase()：将字符串转为大写字母；

#### 抽象类必须要有抽象方法吗？

不需要，抽象类不一定非要有抽象方法。

#### 普通类和抽象类有哪些区别？

- 普通类不能包含抽象方法，抽象类可以包含抽象方法；
- 普通类可以直接实例化，抽象类不能直接实例化。

#### 抽象类能使用 final 修饰吗？

不能，抽象类就是让其他类继承的，被final修饰的类不能被继承，这样就矛盾了，所以抽象类不能使用final修饰。

#### 接口和抽象类有什么区别？

- 实现：接口是被实现的，使用implements来实现接口，而抽象类是被继承的，用extends来继承；
- 构造函数：接口没有构造函数，抽象类有；
- 实现数量：类可以实现多个接口，但是只能继承一个抽象类；
- 访问修饰符：接口中的方法默认使用public修饰；抽象类中的方法可以是任意访问修饰符。

#### java 中 IO 流分为几种？

按功能来分有两种：输入流（input）、输出流（output）。

按类型来分：字节流和字符流。

字节流和字符流的区别是：字节流按8位传输以字节为单位输入输出数据，字符流按16位传输以字符流为单位输入输出数据。

#### BIO、NIO、AIO 有什么区别？

- BIO：Block IO 同步阻塞式IO，平时使用的传统IO，模式简单使用方便，但是并发处理能力低；
- NIO：New IO 同步非阻塞IO，传统IO的升级，客户端和服务端通过Channel（通道）通讯，实现了多路复用；
- AIO：Asynchronous IO 是 NIO 的升级，又称为 NIO2，实现了异步非阻塞IO，异步IO的操作基于事件和回调机制。

#### Files的常用方法都有哪些？

java.nio.file.Files：

- Files.exists()：检测文件是否存在；
- Files.createFile()：创建文件；
- FIles.createDirectory()：创建文件夹；
- Files.delete()：删除文件；
- Files.copy()：复制文件；
- Files.move()：移动文件；
- FIles.size()：查看文件个数；
- Files.read()：读取文件；
- FIles.write()：写入文件。