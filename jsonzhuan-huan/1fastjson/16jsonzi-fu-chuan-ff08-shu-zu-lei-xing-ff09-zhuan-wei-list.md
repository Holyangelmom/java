### 1.6、JSON字符串（数组类型）转为List&lt;&gt;

```java
private static final String  JSON_ARRAY_STR = "[
{\"studentName\":\"lily\",\"studentAge\":12},
{\"studentName\":\"lucy\",\"studentAge\":15}
]";


List<Student> students = JSON.parseObject(json,new TypeReference<List<Student>>(){});
```



