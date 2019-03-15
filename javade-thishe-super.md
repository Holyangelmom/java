# Java的super和this

### 一、super

##### （1）super的意义

super关键字表示对某个类的父类的引用，通常用来访问父类的方法、变量、构造方法（private类型的除外）。

##### （2）super的用法

① 访问父类变量：super.count

② 访问父类方法：super.print\(\)

③ 访问父类构造方法，但必须要写在构造方法内第一行，因为构造子类前需构造父类：super\(\)或者super\(...\)

### 二、this

##### （1）this的意义

this代表着当前对象的引用或者当前对象的地址。

