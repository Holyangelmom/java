### for/foreach/iterator遍历效率对比

##### 1、ArrayList和LinkedList三种遍历速度

![](/assets/ArrayList遍历速度.png)

![](/assets/linkedList遍历结果.png)

事实证明ArrayList使用for遍历速度最快，LinkedList使用foreach、iterator遍历速度最快。而LinkedList的foreach是用iterator实现的。

