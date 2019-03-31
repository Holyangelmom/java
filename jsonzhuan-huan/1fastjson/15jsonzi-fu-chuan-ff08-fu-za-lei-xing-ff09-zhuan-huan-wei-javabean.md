### 1.5、JSON字符串（复杂类型）转换为JavaBean

```java


public static void test(){

    ArrayList<Student> students = JSON.parseObject(JSON_ARRAY_STR, new TypeReference<ArrayList<Student>>() {});
    //ArrayList<Student> students1 = JSONArray.parseObject(JSON_ARRAY_STR, new TypeReference<ArrayList<Student>>() {});//因为JSONArray继承了JSON，所以这样也是可以的

    for (Student student : students) {
        System.out.println(student.getStudentName()+":"+student.getStudentAge());
    }
}
```



