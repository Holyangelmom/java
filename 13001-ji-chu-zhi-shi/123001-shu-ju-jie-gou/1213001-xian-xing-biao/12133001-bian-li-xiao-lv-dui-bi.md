### for/foreach/iterator遍历效率对比

##### 1、ArrayList和LinkedList三种遍历速度

![](/assets/ArrayList遍历速度.png)

![](/assets/linkedList遍历结果.png)

事实证明ArrayList使用for遍历速度最快，LinkedList使用foreach、iterator遍历速度最快。而LinkedList的foreach是用iterator实现的。

##### 2、for和iterator的foreach实现方式

对于collection，若想使用foreach循环遍历，则必须实现Iterable接口；而对于数组，当使用foreach循环遍历时，网上有网友说是jdk将foreach循环转化为对数组的引用。

对于collection，foreach内部语法是通过nested iteration来实现的；对于array，forreach是通过下标遍历来实现。实际上它们内部都是先将当前下标元素或下个元素转换为foreach指定的类型。下面是两张foreach实现对比图：

![](/assets/foreach两种实现.png)

3、

