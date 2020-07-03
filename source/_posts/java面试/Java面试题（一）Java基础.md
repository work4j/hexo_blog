---
title: Java面试题汇总（一）Java基础
date: 2019-03-13 11:43:51
tags:
- java
- 面试题
- 面试
---

## [Java面试题汇总](/2019/03/13/java面试/Java面试题汇总/)（一）Java基础

1. #### JDK和JRE有什么区别？

   - JDK：Java Development Kit 的简称，java 开发工具包，提供了 java 的开发环境和运行环境。
   - JRE：Java Runtime Environment 的简称，java 运行环境，为 java 的运行提供了所需环境。

   其实JDK包含了JRE，同时还包含了编辑java源码的编译器javac，还包含了很多java程序调试和分析的工具，简单来说：如果你需要运行java程序，只需要安装JRE就可以了，如果你还需要编写java程序，需要安装JDK。

2. #### == 和 equals 的区别是什么？

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

3. #### 两个对象的 hashCode()相同，则 equals()也一定为 true，对吗？

   错，两个对象的 hashCode()相同， equals()不一定为 true。

4. #### final 在 java 中有什么作用？

   - final 修饰的类叫最终类，该类不能被继承；
   - final 修饰的方法不能被重写；
   - final 修饰的变量叫常量，常量必须被初始化， 初始化之后就不能被修改。

5. #### java 中的 Math.round(-1.5) 等于多少？

6. #### String 属于基础的数据类型吗？

7. #### java 中操作字符串都有哪些类？它们之间有什么区别？

8. #### String str="i"与 String str=new String("i")一样吗？

9. #### 如何将字符串反转？

10. #### String 类的常用方法都有那些？

11. #### 抽象类必须要有抽象方法吗？

12. #### 普通类和抽象类有哪些区别？

13. #### 抽象类能使用 final 修饰吗？

14. #### 接口和抽象类有什么区别？

15. #### java 中 IO 流分为几种？

16. #### BIO、NIO、AIO 有什么区别？

17. #### Files的常用方法都有哪些？