### ArrayList 中 elementData 为什么使用 transient 修饰？

```java
transient Object[] elementData;
```

由于 ArrayList 是基于动态数组实现的，所以并不是所有的空间都被使用。因此使用了 transient 修饰，不会被虚拟机进行默认的序列化。虽说不会被jvm默认序列化，但ArrayList自定义了序列化。看下源代码，它序列化的长度为`size`。再看下`size`的定义

![](/assets/ArrayList序列化.png)

定义为`其包含的元素的个数`，说明不是ArrayList动态扩容后的length。

![](/assets/ArrayList-size.png)



