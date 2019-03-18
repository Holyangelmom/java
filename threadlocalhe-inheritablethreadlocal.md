# ThreadLocal和InheritableThreadLocal

### 1、参考资料

https://www.jianshu.com/p/a1d4cce7af53

### 2、ThreadLocal是什么？

ThreadLocal提供了thread-local的变量。这些变量不同于它们自身正常的形态——每个线程通过自身get或set方法访问thread-local变量时，访问到的都是thread-local变量的副本，也就是说每个线程在使用该变量时互不干扰。



