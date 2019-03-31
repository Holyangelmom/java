### 1.6、JSON字符串（简单类型）转为List&lt;&gt;

先给JSON字符串（简单类型）加上数组符号，再转为List&lt;&gt;。

```java
private static final String  JSON_OBJ_STR = "{\"studentName\":\"lily\",\"studentAge\":12}";


public static void test(){
    JSON_OBJ_STR = "[" + JSON_OBJ_STR + "]";
    List<Student> students = JSON.parseObject(json,new TypeReference<List<Student>>(){});
}
```



