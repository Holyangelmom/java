### 1.2.1、线性表

线性表分为链式存储、顺序存储两种，典型的代表就是LinkedList和ArrayList。LinkedList和ArrayList两种线性表的基本实现方式在大学课堂上都讲过，下面着重分析这两种线性表增删改查的时间复杂度，以及它们在实现时用到的特殊思想或算法。

##### 1、时间复杂度

（1）查找

对比：

ArrayList查找元素的时间复杂度：O\(n\)

LinkedList查找元素的时间复杂度：O\(n\)

简述：

一个使用for循环，一个使用while循环 ，长度都为n，所以时间复杂度为O\(n\)。

（2）获取

对比：

ArrayList获取元素的时间复杂度：O\(1\)

LinkedList获取元素的时间复杂度：O\(n\)

简述：

ArrayList直接返回指定下标的元素，而LinkedList先判断指定下标是否小于size/2，判断靠近头部还是尾部再移动“指针”到指定位置，源码如下：

![](/assets/linkedList-get%28%29.png)



