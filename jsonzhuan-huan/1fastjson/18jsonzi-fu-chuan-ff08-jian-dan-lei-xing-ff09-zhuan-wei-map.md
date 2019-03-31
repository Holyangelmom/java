### 1.8、JSON字符串（简单类型）转为Map

```java
private static final String  JSON_OBJ_STR = "{\"studentName\":\"lily\",\"studentAge\":12}";


public static void test(){
    //用这种方法没有类型安全警告
    JSONObject  jsonObject = JSONObject.parseObject(JSON_OBJ_STR);
    
    Map<String,Object> map = (Map<String,Object>)jsonObject;
}
```



