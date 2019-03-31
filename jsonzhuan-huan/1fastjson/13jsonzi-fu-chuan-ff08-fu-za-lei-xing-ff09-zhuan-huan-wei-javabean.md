### 1.3、JSON字符串（复杂类型）转换为JavaBean

```java
private static final String  JSON_OBJ_STR = "{\"studentName\":\"lily\",\"studentAge\":12}";



public static void test(){

    Student student = JSON.parseObject(JSON_OBJ_STR, Student.class);
    System.out.println(student.getStudentName()+":"+student.getStudentAge());

}
```



