# Java与Oracle的日期、时间类型

### 1、参考资料

[https://www.jianshu.com/p/5e4b4e7785e4](https://www.jianshu.com/p/5e4b4e7785e4)

[https://blog.csdn.net/qq\_33573235/article/details/78154928](https://blog.csdn.net/qq_33573235/article/details/78154928)

### 2、Java常用时间或日期的

**（1）Hierarchy**

![](/assets/时间或日期类继承图.png)

**（2）时间精度**

| 类型 | java.util.Date | java.sql.Timestamp | java.sql.Date |
| :--- | :--- | :--- | :--- |
| 精度 | 年 月 日 时 分 秒 | 年 月 日 时 分 秒 毫 微秒 | 年 月 日 |

### 3、Oracle常用时间或日期

**（1）Date**

ORACLE最常用的日期类型，它可以保存日期和时间，常用日期处理都可以采用这种类型。DATE表示的日期范围可以是公元前4712年1月1日至公元9999年12月31日。 

**（2）Timestamp**

ORACLE常用的日期类型，它与Date的区别是不仅可以保存日期和时间，还能保存小数秒，小数位数可以指定为0-9，默认为6位。除此以外，Timestamp与Date类型功能相同。

### 4、日期或时间从Java到Oracle的转换

**（1）Oracle字段类型为Date**

第一种：利用Oracle中的方法to\_date\(\)， 在sql语句中使用to\_date\(\)方法。

第二种：在代码中使用java.sql.Date（但只能精确到年月日）。为什么不用java.util.Date？因为java.util.Date 就是在除了SQL语句的情况下面使用，java.sql.Date 是针对SQL语句使用的。

第三种：在代码中使用java.sql.Timestamp（精确到微秒）

**（2）Oracle字段类型为Timestamp**

（预留）

