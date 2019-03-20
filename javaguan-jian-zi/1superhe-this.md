# super和this

### 1、super

##### （1）super的意义

super关键字表示对某个类的父类的引用，通常用来访问父类的方法、变量、构造方法（private类型的除外）。另外super不可以在static环境中使用，包括：static变量,static方法，static语句。

##### （2）super的用法

① 访问父类变量：super.count

② 访问父类方法：super.print\(\)

③ 访问父类构造方法，但必须要写在构造方法内第一行，因为构造子类前需构造父类：super\(\)或者super\(...\)

### 2、this

##### （1）this的意义

this代表着当前对象的引用或者当前对象的地址。this和super的用法大致相同，但this的含义比较复杂。另外this不可以在static环境中使用，包括：static变量,static方法，static语句。

##### （2）this的用法

① 访问当前对象的变量：this.count

② 访问当前对象的方法：this.print\(\)

③ 访问当前对象的构造方法，但this和super不能同时出现在一个构造函数里面：this\(\)或者this\(...\)

##### （3）this最容易混淆的地方

```java
package cn.test;
public class A {
    public void test() {
        System.out.println(this.getClass().getName());
    }
}

package cn.test;
public class B extends A{
    public static void main(String[] args) {
        B b = new B();
        b.test();
    }
}

输出：cn.test.B
```

在继承关系中，不管父类还是子类，这些类里面的this都代表了最终new出来时的那个类型的实例对象，所以在父类中你可以中this获取到子类的信息！

