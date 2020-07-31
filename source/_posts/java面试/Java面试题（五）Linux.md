---
title: Java面试题汇总（五）Linux
date: 2019-03-13 11:43:51
tags:
- java
- 面试题
- 面试
- Linux
---

## [Java面试题汇总](/2019/03/13/java面试/Java面试题汇总/)（五）Linux

#### 常用的查看文件内容命令有哪些？

tail  cat  more  vi  vim

#### 怎么查找特定的文件？

find命令

语法：find path [options] params

作用：在指定目录下查找文件

举例：

- find ~ -name "target.java"	//精确查找文件
- find ~ -name "target*"   //模糊查找文件
- find ~ -iname "target*"   //不区分文件名大小写去查找文件

#### 检索文件内容？

grep命令（Global Regular Expression Print）

语法：grep [options] pattern file

作用：查找文件里符合条件的字符串

举例：

- grep 'test' target.log   //查找target.log文件里有“test”字符串的行
- grep -o '[a-zA-Z0-9-]'   //根据正则表达式进行匹配查找
- grep -v 'test'  //找到不匹配“test”的行

grep经常搭配 **管道操作符 |**

作用：可将指令连接起来，前一个指令的输出作为后一个指令的输入

举例：

- ps -ef | grep tomcat   //查找tomcat进程

#### 对文件内容做统计？

awk命令

语法：awk [options] 'cmd' file

作用：

- 一次读取一行文本，对输入分隔符进行切片，切成多个组成部分；
- 将切片直接保存在内建的变量中，$1,$2...($0表示行的全部)；
- 支持对单个切片的判断，支持循环判断，默认分隔符为空格；

举例：

- awk '{print $1,$4}' netstat.txt   //默认以空格为分隔符对每行数据切片后，输出第1和第4列数据
- awk -F "," '{print $1,$4}' netstat.txt   //以",为分隔符对每行数据切片后，输出第1和第4列数据
- awk '$1=="tcp" && $2==1 {print $0}' netstat.txt   //输出第1列数据为”tcp“，第2列数据为1的所有行数据
- awk '{arr[$1]++}END{for(i in arr)print i "\t" arr[i]}'   //定义了一个名字叫arr的数组，$1中遇到相同项就加一，然后循环输出个数

#### 批量替换文本内容？

sed命令（stream editor 流编辑器）

语法：sed [options] 'sed command' filename

作用：适合用于对文本的行内容进行处理

