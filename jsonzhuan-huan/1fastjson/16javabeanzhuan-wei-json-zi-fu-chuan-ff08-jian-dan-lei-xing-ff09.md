### 1.6、JavaBean、List&lt;&gt;转为JSON字符串

```java
    //JavaBean转为JSON字符串
    Data data = new Data();
    data.setAction("add");
    data.setId("1");
    String s = JSON.toJSONString(data);
    
    
    
    //List<>转为JSON字符串
    List<Student> students = new ArrayList();
    students.add(...);
    students.add(...);
    String jsonStr = JSON.toJSONString(students);
```



