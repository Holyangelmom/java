### 1.5、JSON字符串（复杂类型）转换为JavaBean

```java
private static final String  COMPLEX_JSON_STR = "
{\"teacherName\":\"crystall\",\"teacherAge\":27,
    \"course\":{\"courseName\":\"english\",\"code\":1270},\
    "students\":[{\"studentName\":\"lily\",\"studentAge\":12},{\"studentName\":\"lucy\",\"studentAge\":15}]
}";




public static void test(){

    Teacher teacher = JSON.parseObject(COMPLEX_JSON_STR, new TypeReference<Teacher>() {});
    //Teacher teacher1 = JSON.parseObject(COMPLEX_JSON_STR, new TypeReference<Teacher>() {});//因为JSONObject继承了JSON，所以这样也是可以的
    String teacherName = teacher.getTeacherName();
    Integer teacherAge = teacher.getTeacherAge();
    Course course = teacher.getCourse();
    List<Student> students = teacher.getStudents();
}
```



