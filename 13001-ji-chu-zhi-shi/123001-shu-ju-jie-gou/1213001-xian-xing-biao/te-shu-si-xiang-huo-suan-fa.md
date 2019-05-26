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

![](/assets/foreach删除元素报错.png)**（2）fail-fast和fail-safe机制**



