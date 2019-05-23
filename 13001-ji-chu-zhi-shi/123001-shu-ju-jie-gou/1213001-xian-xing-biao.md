### 1.2.1、线性表

线性表分为链式存储、顺序存储两种，典型的代表就是LinkedList和ArrayList。LinkedList和ArrayList两种线性表的基本实现方式在大学课堂上都讲过，下面着重分析这两种线性表增删改查的时间复杂度，以及它们在实现时用到的特殊思想或算法。

##### 1、时间复杂度

**（1）查找**

对比：

ArrayList查找元素的时间复杂度：O\(n\)

LinkedList查找元素的时间复杂度：O\(n\)

简述：

一个使用for循环，一个使用while循环 ，长度都为n，所以时间复杂度为O\(n\)。

**（2）获取**

对比：

ArrayList获取元素的时间复杂度：O\(1\)

LinkedList获取元素的时间复杂度：O\(n/2\)

简述：

ArrayList直接返回指定下标的元素，而LinkedList先判断指定下标是否小于size/2，判断靠近头部还是尾部再移动“指针”到指定位置，源码如下：

![](/assets/linkedList-get%28%29.png)

**（3）插入**

对比：

ArrayList插入元素的时间复杂度：O\(n\)

LinkedList插入元素的时间复杂度：O\(1\)

简述：

ArrayList的add\(E\)方法直接在末尾插入，而add\(i, E\)方法是调用System.arraycopy\(\)方法将i之后的元素都插入到后边的位置，最坏时要移动全部元素n，所以时间复杂度为O\(n\)。而LinkedList插入元素只需要在指定位置修改元素的双向指针即可，所以时间复杂度为O\(1\)。

**（4）修改**

对比：

ArrayList修改元素的时间复杂度：O\(1\)

LinkedList修改元素的时间复杂度：O\(n/2\)

简述：

（和元素的获取一样）

**（5）删除**

对比：

ArrayList删除元素的时间复杂度：O\(n\)

LinkedList删除元素的时间复杂度：O\(1\)

简述：

（和元素的插入一样）











