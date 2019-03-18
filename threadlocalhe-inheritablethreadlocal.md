# ThreadLocal和InheritableThreadLocal

### 1、参考资料

[https://www.jianshu.com/p/a1d4cce7af53](https://www.jianshu.com/p/a1d4cce7af53)

### 2、ThreadLocal是什么？

ThreadLocal提供了thread-local的变量。这些变量不同于它们自身正常的形态——每个线程通过自身get或set方法访问thread-local变量时，访问到的都是thread-local变量的副本，也就是说每个线程在使用该变量时互不干扰。

### 3、ThreadLocal源码跟踪

我直接在项目中找了个例子，跟踪一下。先是ThreadLocal的get\(\)方法。

![](/assets/ThreadLocal.get.png)

浏览一下源码，首先获取当前线程的ThreadLocalMap对象，若不为空则返回ThreadLocalMap对象的value，否则返回setInitialValue\(\)。

![](/assets/ThreadLocal.get的detail.png)

再看看ThreadLocalMap这玩意儿，实际上是ThreadLocal自定义的hash map，用于维护线程本地的values。再看看map内部还有一个Entry类，它继承WeakReference&lt;ThreadLocal&lt;?&gt;&gt;，也就限制ThreadLocalMap只能存储ThreadLocalMap。再看看Entry类内部只有一个value对象，该对象存储了最终的对象。





![](/assets/ThreadLocal.ThreadLocalMap定义.png)

















