### 1.6、JavaBean转为JSON字符串

```java
    Data data = new Data();
    data.setAction("add");
    data.setId("1");

    String s = JSON.toJSONString(data);
```



