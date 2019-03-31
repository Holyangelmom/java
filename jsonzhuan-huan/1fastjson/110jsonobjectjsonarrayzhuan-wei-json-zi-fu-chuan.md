### 1.10、JSONObject、JSONArray转为JSON字符串

使用JSONObject、JSONArray的对象的toString或者toJSONString方法。

```java
JSONObject jsonO = ...;
JSONArray jsonA = ...;

String o = jsonO.toString();
String o2 = jsonO.toJSONString();


String array = jsonA.toString();
String array2 = jsonA.toJSONString();
```



