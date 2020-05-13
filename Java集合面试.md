**1）说说常见的集合有哪些吧？**

答：Map接口和Collection接口是所有集合框架的父接口：

1.  Collection接口的子接口包括：Set接口和List接口

2.  Map接口的实现类主要有：HashMap、TreeMap、Hashtable、ConcurrentHashMap以及Properties等

3.  Set接口的实现类主要有：HashSet、TreeSet、LinkedHashSet等

4.  List接口的实现类主要有：ArrayList、LinkedList、Stack以及Vector等

**（2）HashMap和Hashtable的区别有哪些？（必问）**

答：

1.  HashMap没有考虑同步，是线程不安全的；Hashtable使用了synchronized关键字，是线程安全的；

2.  前者允许null作为Key；后者不允许null作为Key

**3）HashMap的底层实现你知道吗？**

答：在Java8之前，其底层实现是数组+链表实现，Java8使用了数组+链表+红黑树实现。此时你可以简单的在纸上画图分析：

![enter image description here](https://upload-images.jianshu.io/upload_images/11474088-482713cf687c78fb?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**4）ConcurrentHashMap和Hashtable的区别？**必问

答：ConcurrentHashMap结合了HashMap和HashTable二者的优势。HashMap没有考虑同步，hashtable考虑了同步的问题。但是hashtable在每次同步执行时都要锁住整个结构。 ConcurrentHashMap锁的方式是稍微细粒度的。 ConcurrentHashMap将hash表分为16个桶（默认值），诸如get,put,remove等常用操作只锁当前需要用到的桶。

**面试官：ConcurrentHashMap的具体实现知道吗？**

答：

1.  该类包含两个静态内部类HashEntry和Segment；前者用来封装映射表的键值对，后者用来充当锁的角色；

2.  Segment是一种可重入的锁ReentrantLock，每个Segment守护一个HashEntry数组里得元素，当对HashEntry数组的数据进行修改时，必须首先获得对应的Segment锁。

**5）HashMap的长度为什么是2的幂次方？**

答：

1.  通过将Key的hash值与length-1进行&运算，实现了当前Key的定位，2的幂次方可以减少冲突（碰撞）的次数，提高HashMap查询效率

2.  如果length为2的次幂 则length-1 转化为二进制必定是11111……的形式，在于h的二进制与操作效率会非常的快，而且空间不浪费；如果length不是2的次幂，比如length为15，则length-1为14，对应的二进制为1110，在于h与操作，最后一位都为0，而0001，0011，0101，1001，1011，0111，1101这几个位置永远都不能存放元素了，空间浪费相当大，更糟的是这种情况中，数组可以使用的位置比数组长度小了很多，这意味着进一步增加了碰撞的几率，减慢了查询的效率！这样就会造成空间的浪费。

**6）List和Set的区别是啥？**

答：List元素是有序的，可以重复；Set元素是无序的，不可以重复。

**7）List、Set和Map的初始容量和加载因子：**

答：

**1\. List**

*  **ArrayList**的初始容量是10；加载因子为0.5； 扩容增量：原容量的 0.5倍+1；一次扩容后长度为16。

*  **Vector**初始容量为10，加载因子是1。扩容增量：原容量的 1倍，如 Vector的容量为10，一次扩容后是容量为20。

**2\. Set**

**HashSet**，初始容量为16，加载因子为0.75； 扩容增量：原容量的 1 倍； 如 HashSet的容量为16，一次扩容后容量为32

**3\. Map**

HashMap，初始容量16，加载因子为0.75； 扩容增量：原容量的 1 倍； 如 HashMap的容量为16，一次扩容后容量为32

**8）Comparable接口和Comparator接口有什么区别？**

答：

1.  前者简单，但是如果需要重新定义比较类型时，需要修改源代码。

2.  后者不需要修改源代码，自定义一个比较器，实现自定义的比较方法。

**9）Java集合的快速失败机制“fail-fast”**

答：

是java集合的一种错误检测机制，当多个线程对集合进行结构上的改变的操作时，有可能会产生fail-fast机制。

**例如**：假设存在两个线程（线程1、线程2），线程1通过Iterator在遍历集合A中的元素，在某个时候线程2修改了集合A的结构（是结构上面的修改，而不是简单的修改集合元素的内容），那么这个时候程序就会抛出 ConcurrentModificationException 异常，从而产生fail-fast机制。

**原因：**迭代器在遍历时直接访问集合中的内容，并且在遍历过程中使用一个 modCount 变量。集合在被遍历期间如果内容发生变化，就会改变modCount的值。每当迭代器使用hashNext()/next()遍历下一个元素之前，都会检测modCount变量是否为expectedmodCount值，是的话就返回遍历；否则抛出异常，终止遍历。

**解决办法：**

1.  在遍历过程中，所有涉及到改变modCount值得地方全部加上synchronized。

2.  使用CopyOnWriteArrayList来替换ArrayList
