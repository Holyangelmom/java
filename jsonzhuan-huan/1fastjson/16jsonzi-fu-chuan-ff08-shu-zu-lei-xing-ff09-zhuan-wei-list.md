### 1.6、JSON字符串（数组类型）转为List&lt;&gt;

实际上和JSON字符串（数组类型）转换为JavaBean一样。

```java
private static final String  JSON_ARRAY_STR = "[
{\"studentName\":\"lily\",\"studentAge\":12},
{\"studentName\":\"lucy\",\"studentAge\":15}
]";


List<Student> students = JSON.parseObject(json,new TypeReference<List<Student>>(){});
```



