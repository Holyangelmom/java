# ThreadLocal和InheritableThreadLocal

### 1、参考资料

[https://www.jianshu.com/p/a1d4cce7af53](https://www.jianshu.com/p/a1d4cce7af53)

[https://www.jianshu.com/p/98b68c97df9b](https://www.jianshu.com/p/98b68c97df9b)

[https://www.jianshu.com/p/56f64e3c1b6c](https://www.jianshu.com/p/56f64e3c1b6c)

[https://www.jianshu.com/p/a1cd61fa22da](https://www.jianshu.com/p/a1cd61fa22da)

### 2、ThreadLocal

##### （1）ThreadLocal是什么？

ThreadLocal提供了thread-local的变量。这些变量不同于它们自身正常的形态——每个线程通过自身get或set方法访问thread-local变量时，访问到的都是thread-local变量的副本，也就是说每个线程在使用该变量时互不干扰。我在参考资料的模型图基础上改了一下，做了以下这张模型图。

![](/assets/ThreadLocal在各线程的模型图.png)再贴一张参考资料的ThreadLocal在堆栈中的结构图。

![](/assets/ThreadLocal堆栈结构图.png)

##### （2）、ThreadLocal源码跟踪

我直接在项目中找了个例子，跟踪一下。先是ThreadLocal的get\(\)方法。

![](/assets/ThreadLocal.get.png)

浏览一下源码，首先获取当前线程的ThreadLocalMap对象，若不为空则返回ThreadLocalMap对象的value，否则返回setInitialValue\(\)。

![](/assets/ThreadLocal.get的detail.png)

先看看ThreadLocalMap这玩意儿，实际上是ThreadLocal自定义的hash map，用于维护线程本地的values。再看看map内部还有一个Entry类，它继承WeakReference&lt;ThreadLocal&lt;?&gt;&gt;——（弱引用，生命周期只能存活到下次GC前），也就限制ThreadLocalMap只能存储ThreadLocal类型的对象。再看看Entry类内部只有一个value对象，存储了最终的对象。

![](/assets/ThreadLocal.ThreadLocalMap定义.png)

再看看ThreadLocal.get\(\)中的getMap\(t\)，它直接return当前线程的threadLocals变量，再看看threadLocals这玩意儿，实际上是一个

ThreadLocal.ThreadLocalMap对象，该map就是由ThreadLocal内部维护。

![](/assets/threadLocals定义.png)

最后看看ThreadLocal.get\(\)中最后return的setInitialValue\(\)方法，实际上和set\(\)方法差不多，都先判断map是否为空，若不为空，则设置value值，否则创建map后再set value。

![](/assets/setInitialValue方法.png)

##### （3）ThreadLocal核心

核心代码有点复杂，看了些资料，暂时没时间整理，先记录一下两种地址算法的思想：**开放地址法、链表法。**

**开放地址法：**

经过某种hash算法计算出地址后，查看该地址是否已存有数据。若无，则存入数据；否则当发生地址冲突时，按照某种方法继续探测哈希表中的其他存储单元，直到找到空位置为止。

**链表法：**

经过某种hash算法计算出地址后，查看该地址是否已存有数据。若无，则存入数据；否则将待插入的数据链接到当前链表尾部或头部。

##### （4）ThreadLocalMap的hash冲突问题

问题描述（copy一下参考资料）：

ThreadLocalMap中解决Hash冲突采用了线性探测的方式，就是简单的步长加1或减1，寻找下一个相邻的位置。显然ThreadLocalMap采用线性探测的方式解决Hash冲突的效率很低。如果有大量不同的ThreadLocal对象放入map中时发送冲突，或者发生二次冲突，则效率很低。

个人想法：

个人感觉在ThreadLocal的应用场景中不会有大量的数据存储，较为合理的开放地址法使hash冲突很少，即使有冲突利用简单的线性查找方法足以解决。

**（5）ThreadLocalMap内存泄漏问题**

问题描述（copy一下参考资料）：

前面提到，map内部还有一个Entry类，在构造方法中定义key为弱引用（Entry\(ThreadLocal&lt;?&gt; k, Object v\) ）。弱引用是什么鬼还不知道，查了资料说发生GC时弱引用Key会被回收。key是弱引用，value是强引用，则key被回收时，value不会被回收。若线程一直运行则可能发生内存泄漏。尽管jvm团队采取一些措施防止ThreadLocalMap内存泄漏，但如此也并不能保证ThreadLocal不会发生内存泄漏，详情参考[https://www.jianshu.com/p/a1cd61fa22da。](https://www.jianshu.com/p/a1cd61fa22da。)

想法（copy一下参考资料）：

既然Key是弱引用，那么我们要做的事，就是在调用ThreadLocal的get\(\)、set\(\)方法时完成后再调用remove方法，将Entry节点和Map的引用关系移除，这样整个Entry对象在GC Roots分析后就变成不可达了，下次GC的时候就可以被回收。

### 3、InheritableThreadLocal

##### （1）InheritableThreadLocal是什么？

ThreadLocal固然很好，但是子线程并不能取到父线程的ThreadLocal的变量。而InheritableThreadLocal可以解决这个问题。

