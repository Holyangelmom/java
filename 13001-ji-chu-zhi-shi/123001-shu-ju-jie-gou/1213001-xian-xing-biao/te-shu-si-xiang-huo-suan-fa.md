### 特殊点或算法

##### 1、为什么阿里禁止在 foreach 循环里进行元素的 remove/add 操作

**（1）开头**

这里援引一篇文章，[https://my.oschina.net/u/3959491/blog/3048106 ](https://my.oschina.net/u/3959491/blog/3048106)，专门讲解禁止在foreach循环中删除或新增元素。通常我会使用foreach遍历顺序存储的collection，但确实没在foreach里删除或新增过元素，索性照着文章代码试下，果然抛出异常。之所以会出现这个异常，是因为触发了一个Java集合的错误检测机制——fail-fast 。

```java
List<String> userNames = new ArrayList<String>() {{
    add("Hollis");
    add("hollis");
    add("HollisChuang");
    add("H");
}};

for (String userName : userNames) {
    if (userName.equals("Hollis")) {
        userNames.remove(userName);
    }
}

System.out.println(userNames);
```

![](/assets/foreach删除元素报错.png)**（2）什么是fail-fast机制？**

fail-fast 机制是java集合\(Collection\)中的一种错误机制，JDK并不保证fail-fast机制一定会发生。有两种情况下会产生fail-fast事件：

* 当多个线程对同一个集合的内容进行操作时，就可能会通过抛出ConcurrentModificationException来产生fail-fast事件。
* 即使不是多线程环境，如果单线程违反了规则，同样也有可能会抛出改异常。

对于上述两种情况分别举例：

* 当某一个线程A通过iterator去遍历某集合的过程中，若该集合的内容被其他线程所改变了；那么线程A访问集合时，就会抛出ConcurrentModificationException异常，产生fail-fast事件。
* 当使用foreach遍历collection时，对collection进行删除/新增操作也会产生fail-fast事件。

##### （3）fail-fast原理

产生fail-fast事件，是通过抛出ConcurrentModificationException异常来触发的。那么，ArrayList是如何抛出ConcurrentModificationException异常的呢?在上述代码抛出的异常中跟踪一下，发现进入到ArrayList内部类Itr的next\(\)方法中，因为foreach是基于iterator实现的。再往下执行，调用内部类Itr的checkForComodification\(\)方法。

![](/assets/foreach调用next方法.png)

当ArrayList发现`modCount != expectedModCount时抛出`ConcurrentModificationException。

![](/assets/Itr-checkForComodification.png)

查看一下变量modCount和expectedModCount分别代表啥：

* modCount是AbstractList的成员变量，被ArrayList继承。它表示该集合实际被修改的次数。
* expectedModCount 是 ArrayList中的一个内部类——Itr中的成员变量。expectedModCount表示这个迭代器期望该集合被修改的次数。其值是在ArrayList.iterator方法被调用的时候初始化的。只有通过迭代器对集合进行操作，该值才会改变。

在开头的foreach代码中，删除元素调用的是ArrayList的remove方法，再进一步跟踪发现调用了fastRemove方法。在fastRemove方法中只对modCount变量进行修改，并没有修改expectedModCount，因此删除元素后foreach往下遍历时发现`modCount != expectedModCount`，抛出异常。

![](/assets/fastRemove.png)

