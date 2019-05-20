### volatile

##### 1、参考资料

[https://www.cnblogs.com/zhengbin/p/5654805.html](https://www.cnblogs.com/zhengbin/p/5654805.html)

##### 2、volatile特点

* 可见性
* 禁止指令重排（有序性）

##### 3、可见性

![](/assets/多线程内存图.png)

当对非 volatile 变量进行读写的时候，每个线程先将变量从线程内存拷贝到CPU缓存，再将cpu缓存写入主存（但写入时间不定）。

**若变量被 volatile修饰，则保证了新值能立即同步到主内存，以及每次使用前立即从主内存刷新。JVM 保证了每次读变量都从内存中读，跳过 CPU cache 这一步。**

##### 4、禁止指令重排序优化（有序性）

指令重排序：是指CPU采用了允许将多条指令不按程序规定的顺序分开发送给各相应电路单元处理。

```java
//x、y为非volatile变量

//flag为volatile变量
 
x = 2;        //语句1
y = 0;        //语句2
flag = true;  //语句3
x = 4;         //语句4
y = -1;       //语句5
```



