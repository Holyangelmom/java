# 浅谈Java与Oracle的日期、时间类型

### 1、参考资料

https://www.jianshu.com/p/5e4b4e7785e4

https://blog.csdn.net/qq\_33573235/article/details/78154928

### 2、Java常用时间或日期的Hierarchy

![](/assets/时间或日期类继承图.png)

### 3、Oracle常用时间或日期

**（1）Date**

ORACLE最常用的日期类型，它可以保存日期和时间，常用日期处理都可以采用这种类型。DATE表示的日期范围可以是公元前4712年1月1日至公元9999年12月31日

**（2）Timestamp**

ORACLE常用的日期类型，它与Date的区别是不仅可以保存日期和时间，还能保存小数秒，小数位数可以指定为0-9，默认为6位。除此以外，Timestamp与Date类型功能相同





