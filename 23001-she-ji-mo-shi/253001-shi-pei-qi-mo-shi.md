### 适配器模式

##### 1、定义

将一个类的接口转化为客户希望的另一个接口的模式，叫做适配器模式。

##### 2、分类

适配器模式分为两类：

* 类适配器
* 对象适配器

![](/assets/适配器模式分类.png)

##### 3、UML图

* 目标（Target）角色：定义 Client 使用的接口。
* 被适配（Adaptee）角色：这个角色有一个已存在并使用了的接口，而这个接口是需要我们适配的。
* 适配器（Adapter）角色：这个适配器模式的核心。它将被适配角色已有的接口转换为目标角色希望的接口

![](/assets/适配器模式UML图.png)

##### 4、应用场景

* 旧系统的改造升级
* InputStreamReader\(InputStream\)
* OutputStreamWriter\(OutputStream\)



