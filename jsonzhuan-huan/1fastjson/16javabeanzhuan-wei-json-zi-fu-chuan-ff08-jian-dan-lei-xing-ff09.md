### 1.9、JavaBean、List&lt;&gt;、Map转为JSON字符串

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


    //Map转为JSON字符串
    Map<String, Object> map = new HashMap<String, Object>();
    map.put(...);
    map.put(...);
    String jsonString = JSON.toJSONString(map);
```



