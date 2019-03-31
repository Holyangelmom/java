# 1.1、JSON字符串（简单类型）转换为JSONObject

```java
private static final String  JSON_OBJ_STR = "{\"studentName\":\"lily\",\"studentAge\":12}";

public static void test(){

JSONObject jsonObject = JSON.parseObject(JSON_OBJ_STR);
//JSONObject jsonObject1 = JSONObject.parseObject(JSON_OBJ_STR); //因为JSONObject继承了JSON，所以这样也是可以的

System.out.println(jsonObject.getString("studentName")+":"+jsonObject.getInteger("studentAge"));

}
```



