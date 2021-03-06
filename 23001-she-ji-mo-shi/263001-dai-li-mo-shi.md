### 代理模式

##### 1、定义

给目标对象提供一个代理对象，并由代理对象控制目标对象的引用

##### 1、核心作用

通过代理，在不改变目标对象方法的情况下对方法进行增强。它可以控制某个的方法，在调用这个方法前做前置处理，调用方法后做后置处理，从而实现将统一流程代码放大代理类中处理。

##### 2、UML图

![](/assets/代理模式UML图.png)

##### 3、应用场景

安全代理：屏蔽对真实对象的直接访问。

远程代理：通过代理处理远程方法调用（RMI）。

延迟加载：先加载轻量级的代理对象，真正需要时再加载真实对象。

##### 4、分类

代理模式可分为两种：

* 静态代理：一个具体角色就需要一个代理角色。
* 动态代理：抽象角色中声明的方法都被转移到调用处理器一个统一的方法中处理。这样，我们可以更加灵活和统一的处理众多方法。

##### 5、动态代理

JDK动态代理

-java.lang.reflect.Proxy：动态生成代理类和对象

-java.lang.reflect.InvocationHandler\(处理器接口\)：可通过invoke方法实现对真实角色的代理访问；每次通过Proxy生成代理类对象时都要指定对应的处理器对象。

