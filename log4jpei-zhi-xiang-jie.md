# Log4j配置详解

### 1、log4j概述

日志是应用软件中不可缺少的部分，可帮助开发人员、运维人员快速准确地定位问题所在。Apache的开源项目log4j是一个功能强大的日志组，件提供方便的日志记录。log4j有两种配置方式，一是通过java程序动态设置，二是通过配置文件的方式进行设置。第一种缺点明显，第二种支持两种格式的配置文件：xml文件、properties文件。下面主要讲解xml文件、properties文件的配置方式。

参考资料：

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
> …
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
> …
>
> log4j.appender.appenderName.layout.optionN = valueN

##### （2）基本格式

\#配置根Logger

log4j.rootLogger  =   \[ level \]   ,  appenderName1 ,  appenderName2 ,  …

\#配置日志信息输出目的地Appender

log4j.appender.appenderName  =  fully.qualified.name.of.appender.class

log4j.appender.appenderName.option1  =  value1

…

log4j.appender.appenderName.optionN  =  valueN

\#配置日志信息的格式（布局）

log4j.appender.appenderName.layout  =  fully.qualified.name.of.layout.class

log4j.appender.appenderName.layout.option1  =  value1

…

log4j.appender.appenderName.layout.optionN  =  valueN

##### 

（3）

