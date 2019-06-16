### 可重入锁

##### 1、参考资料

https://blog.csdn.net/u014730165/article/details/82144848

2、可重入锁描述

可重入性描述这样的一个问题：一个线程在持有一个锁的时候，它内部能否再次（多次）申请该锁。如果一个线程已经获得了锁，其内部还可以多次申请该锁成功。那么我们就称该锁为可重入锁。通过以下伪代码说明：

```java
void methodA(){
    lock.lock(); // 获取锁
    methodB();
    lock.unlock() // 释放锁
}

void methodB(){
    lock.lock(); // 获取锁
    // 其他业务
    lock.unlock();// 释放锁
}
```



