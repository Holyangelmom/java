# Log4j配置详解

### 1、log4j概述

日志是应用软件中不可缺少的部分，可帮助开发人员、运维人员快速准确地定位问题所在。Apache的开源项目log4j是一个功能强大的日志组，件提供方便的日志记录。log4j有两种配置方式，一是通过java程序动态设置，二是通过配置文件的方式进行设置。第一种缺点明显，第二种支持两种格式的配置文件：xml文件、properties文件。下面主要讲解xml文件、properties文件的配置方式。

参考资料：[https://blog.csdn.net/azheng270/article/details/2173430/](https://blog.csdn.net/azheng270/article/details/2173430/)

### 2、properties文件配置

##### （1）基本格式

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

##### （2）日志输出级别

level优先级分为OFF、FATAL、ERROR、WARN、INFO、DEBUG、ALL。从右往左，日志信息越来越严重。

（）

