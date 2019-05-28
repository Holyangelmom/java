### ArrayList 为何还要实现 RandomAccess ?

##### 1、先来看看RandomAccess是啥接口？

![](/assets/RandomAccess.png)

咋一看RandomAccess啥方法都没有，通常情况下接口更多的是一种协议、标志，故猜测RandomAccess也是一个标记。再来看看它的定义。

![](/assets/RandomAccess定义.png)

英文不太好就不翻译了，大概的意思就是实现了RandomAccess接口的list支持快速随机访问。如果是实现了这个接口的 List，也就是可以通过`list instanceof RandomAccess `，那么使用for循环的方式获取数据会优于用迭代器获取数据。


