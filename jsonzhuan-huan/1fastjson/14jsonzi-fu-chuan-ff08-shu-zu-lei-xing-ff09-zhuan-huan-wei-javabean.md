### 1.4、JSON字符串（数组类型）转换为JavaBean

```java
private static final String  JSON_ARRAY_STR = "[
{\"studentName\":\"lily\",\"studentAge\":12},
{\"studentName\":\"lucy\",\"studentAge\":15}
]";



public static void test(){

    ArrayList<Student> students = JSON.parseObject(JSON_ARRAY_STR, new TypeReference<ArrayList<Student>>() {});
    //ArrayList<Student> students1 = JSONArray.parseObject(JSON_ARRAY_STR, new TypeReference<ArrayList<Student>>() {});//因为JSONArray继承了JSON，所以这样也是可以的
        
    for (Student student : students) {
        System.out.println(student.getStudentName()+":"+student.getStudentAge());
    }
}
```



