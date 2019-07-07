### 原型模式

##### 1、定义

原型模式（Prototype Pattern）是用于创建重复的对象，同时又能保证性能的模式。这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方式。当直接创建对象的开销比较大时，则采用这种模式。

##### 2、UML图

![](/assets/原型模式UML图.png)

按照原型模式的定义，客户角色不仅要署负责对象的创建，而且还要负责对象的生成和克隆，这样造成客户角色分工不明确，所以我们可以使用一个原型manager来负责对象的创建、生成和克隆。如此一来，客户在使用时向原型manager获取对象的请求，而且还可以修改原型manager的维护的清单，这样就能实现客户不用编码就能实现系统扩展。

![](/assets/原型模式UML图2.png)

上面提到的原型管理器的实现，简单来说就是对原型清单的维护。可以考虑一下几点：

* 要保存一个原型对象的清单，我们可以使用一个 HashMap 来实现，使原型对象和它的名字相对应。
* 原型管理器实现得到、注册、删除原型对象的功能只是对 HashMap 的对应操作而已。
* 原型manager只需要一个就够了，所以可以使用单例模式来实现控制。

3、缺点

没有最完美的工作，只有 最合适的工作。模式亦是如此，任何模式都是有缺陷的。原型模式的主要缺陷是原型必须有clone方法，向已有类添加clone操作比较困难，并且当其内部包括一些不支持 copy 或者循环引用的对象时，实现就更加困难了。
