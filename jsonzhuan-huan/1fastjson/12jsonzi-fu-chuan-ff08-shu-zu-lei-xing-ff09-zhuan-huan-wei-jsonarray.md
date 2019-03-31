# 1.2、JSON字符串（数组类型）转换为JSONArray

```java
private static final String  JSON_ARRAY_STR = "[
{\"studentName\":\"lily\",\"studentAge\":12},
{\"studentName\":\"lucy\",\"studentAge\":15}
]";


public static void test(){

	JSONArray jsonArray = JSON.parseArray(JSON_ARRAY_STR);
	//JSONArray jsonArray1 = JSONArray.parseArray(JSON_ARRAY_STR);//因为JSONArray继承了JSON，所以这样也是可以的

	//遍历方式1
	int size = jsonArray.size();
	for (int i = 0; i < size; i++){
		JSONObject jsonObject = jsonArray.getJSONObject(i);
		System.out.println(jsonObject.getString("studentName")+":"+jsonObject.getInteger("studentAge"));
	}

	//遍历方式2
	for (Object obj : jsonArray) {
		JSONObject jsonObject = (JSONObject) obj;
		System.out.println(jsonObject.getString("studentName")+":"+jsonObject.getInteger("studentAge"));
	}
}

```



