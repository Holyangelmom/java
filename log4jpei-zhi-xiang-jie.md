# Log4j配置详解

### 1、log4j概述

日志是应用软件中不可缺少的部分，可帮助开发人员、运维人员快速准确地定位问题所在。Apache的开源项目log4j是一个功能强大的日志组，件提供方便的日志记录。log4j有两种配置方式，一是通过java程序动态设置，二是通过配置文件的方式进行设置。第一种缺点明显，第二种支持两种格式的配置文件：xml文件、properties文件。下面主要讲解xml文件、properties文件的配置方式。

copy参考资料：

[https://blog.csdn.net/azheng270/article/details/2173430/](https://blog.csdn.net/azheng270/article/details/2173430/)

[https://www.cnblogs.com/byron0918/p/5769646.html](https://www.cnblogs.com/byron0918/p/5769646.html)

### 2、properties文件配置

先讲讲log4j基础知识。

##### （1）日志输出级别

level优先级分为OFF、FATAL、ERROR、WARN、INFO、DEBUG、ALL。从右往左，日志信息越来越严重。

##### （2）根Logger

根logger主要定义log4j支持的日志级别及输出目的地，语法为：log4j.rootLogger=\[level\],appenderName,appenderName,…其中level 是日志记录的优先级，appenderName指定日志信息输出到哪个地方，可同时指定多个输出目的地。

##### （3）package输出级别（子logger）

可以设置不同package的日志输出级别，语法为：

* log4j.logger.packageName=level   （指定package下的输出全为level级别的输出）
* log4j.additivity.packageName=true/false  （log4j.logger默认情况下继承rootLogger的设置。若不想继承rootLogger，该参数可设置为false）

##### （4）输出目的地Appender

Appender定义日志信息输出在什么位置。Log4j提供的appender有以下几种：

* org.apache.log4j.ConsoleAppender（控制台）， 
* org.apache.log4j.FileAppender（文件）， 
* org.apache.log4j.DailyRollingFileAppender（每天产生一个日志文件），
* org.apache.log4j.RollingFileAppender（文件大小到达指定尺寸的时候产生一个新的文件） 
* org.apache.log4j.WriterAppender（将日志信息以流格式发送到任意指定的地方）

Appender主要语法为：

> log4j.appender.appenderName = classInfo
>
> log4j.appender.appenderName.option1 = value1
>
> log4j.appender.appenderName.optionN = valueN

##### （5）日志信息的格式Layout

Layout 负责格式化Appender的输出。Log4j提供的layout有以下几种：

* org.apache.log4j.HTMLLayout（以HTML表格形式布局）
* org.apache.log4j.PatternLayout（可以灵活地指定布局模式）
* org.apache.log4j.SimpleLayout（包含日志信息的级别和信息字符串）
* org.apache.log4j.TTCCLayout（包含日志产生的时间、线程、类别等等信息）

Layout 语法为：

> log4j.appender.appenderName.layout = classInfo
>
> log4j.appender.appenderName.layout.option1 = value1
>
> log4j.appender.appenderName.layout.optionN = valueN

##### （6）日志输出打印参数

> -X号: X信息输出时左对齐；
>
> %p: 输出日志信息优先级，即DEBUG，INFO，WARN，ERROR，FATAL,
>
> %d: 输出日志时间点的日期或时间，默认格式为ISO8601，也可以在其后指定格式，比如：%d{yyy MMM dd HH:mm:ss,SSS}
>
> %r: 输出自应用启动到输出该log信息耗费的毫秒数
>
> %c: 输出日志信息所属的类目，通常就是所在类的全名
>
> %t: 输出产生该日志事件的线程名
>
> %l: 输出日志事件的发生位置，相当于%C.%M\(%F:%L\)的组合,包括类目名、发生的线程，以及在代码中的行数。
>
> %x: 输出和当前线程相关联的NDC\(嵌套诊断环境\)。
>
> %%: 输出一个"%"字符
>
> %F: 输出日志消息产生时所在的文件名称
>
> %L: 输出代码中的行号
>
> %m: 输出代码中指定的消息,产生的日志具体信息
>
> %n: 输出一个回车换行符，Windows平台为"/r/n"，Unix平台为"/n"输出日志信息换行
>
> 可以在%与模式字符之间加上修饰符来控制其最小宽度、最大宽度、和文本的对齐方式。如：
>
> 1\)%20c：指定输出category的名称，最小的宽度是20，如果category的名称小于20的话，默认的情况下右对齐。
>
> 2\)%-20c:指定输出category的名称，最小的宽度是20，如果category的名称小于20的话，"-"号指定左对齐。
>
> 3\)%.30c:指定输出category的名称，最大的宽度是30，如果category的名称大于30的话，就会将左边多出的字符截掉，但小于30的话也不会有空格。
>
> 4\)%20.30c:如果category的名称小于20就补空格，并且右对齐，如果其名称长于30字符，就从左边较远输出的字符截掉。

##### 

##### （7）日志文件输出路径配置

推荐使用两种方式：

使用中间件环境变量：log4j.appender.appendName.File=${catalina.home}/logs/name.log

在web.xml中添加（在非spring项目下试过不成功）：

```
<context-param>
    <param-name>webAppRootKey</param-name>
    <param-value>webApp.root</param-value>  
</context-param>

log4j.properties：
log4j.appender.appendName.File=${webApp.root}logs/log.log
```

##### （8）properties基本格式

> \#配置根Logger
>
> log4j.rootLogger  =   \[ level \]   ,  appenderName1 ,  appenderName2 ,  …
>
> \#配置日志信息输出目的地Appender
>
> log4j.appender.appenderName  =  fully.qualified.name.of.appender.class
>
> log4j.appender.appenderName.option1  =  value1
>
> log4j.appender.appenderName.optionN  =  valueN
>
> \#配置日志信息的格式（布局）
>
> log4j.appender.appenderName.layout  =  fully.qualified.name.of.layout.class
>
> log4j.appender.appenderName.layout.option1  =  value1
>
> log4j.appender.appenderName.layout.optionN  =  valueN

##### 

##### （8）配置样例

\#配置根Logger

log4j.rootLogger=debug,STDOUT



\#子logger

log4j.logger.com.ibatis=debug

log4j.logger.com.ibatis.common.jdbc.SimpleDataSource=debug



\#STDOUT

log4j.appender.STDOUT=org.apache.log4j.ConsoleAppender

log4j.appender.STDOUT.layout=org.apache.log4j.PatternLayout  

log4j.appender.STDOUT.layout.ConversionPattern=%-d{yyyy-MM-dd HH:mm:ss} \[%p\] \[%c\] - %m%n



\#DBACESS MySql

log4j.logger.com.nantian.iwap.persistence.DBAccessMySql=INFO,DBAccessBeanFileAppender

log4j.additivity.com.nantian.iwap.persistence.DBAccessMySql=false

log4j.appender.DBAccessBeanFileAppender=org.apache.log4j.DailyRollingFileAppender

log4j.appender.DBAccessBeanFileAppender.File=${catalina.home}/logs/dbaccess.log

log4j.appender.DBAccessBeanFileAppender.Append=true

log4j.appender.DBAccessBeanFileAppender.Threshold=INFO

log4j.appender.DBAccessBeanFileAppender.layout=org.apache.log4j.PatternLayout

log4j.appender.DBAccessBeanFileAppender.layout.ConversionPattern=\[%r\]\[%d{yyyy-MM-dd HH:mm:ss}\]\[%-5p\] %m%n



