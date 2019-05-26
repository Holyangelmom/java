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

![](/assets/foreach删除元素报错.png)**（2）fail-fast机制**

fail-fast 机制是java集合\(Collection\)中的一种错误机制，JDK并不保证fail-fast机制一定会发生。当多个线程对同一个集合的内容进行操作时，就可能会产生fail-fast事件。

例如：当某一个线程A通过iterator去遍历某集合的过程中，若该集合的内容被其他线程所改变了；那么线程A访问集合时，就会抛出ConcurrentModificationException异常，产生fail-fast事件。



