1. `Collection`:定义独立元素的序列。
2. `Map`：定义成对的键值对（**Key-Value**），一个`Map`不能包含重复的键（**Key**）。
> ![集合](imgs\4.png)


---


## 1. `Collection`和`Iterator`

+ `Collection`接口
   1. `List`代表元素有序的、可重复的。
   2. `Set`代表元素无序、不可重复的集合。
   3. `Queue`代表队列集合，它是一种特殊的线性表，只允许在表的前端删除元素，在表的后端插入元素。
+ `Iterator`
  + 它可以在不知道容器中元素类型的情况下遍历容器中的元素。



## 2.简述`Collection`与`Collections`的区别

1. **java.util.Collection 是一个集合接口**。它提供了对集合对象进行基本操作的通用接口方法。`Collection`接口在*Java*类库中有很多具体的实现。`Collection`接口的意义是为各种具体的集合提供了最大化的统一操作方式。
2. **java.util.Collections 是一个包装类。** 它包含有各种有关集合操作的静态方法（对集合的搜索、排序、线程安全化等），大多数方法都是用来处理线性表的。此类不能实例化，**就像一个工具类，服务于Java的Collection框架**。

## 3.`HashSet`和`TreeSet`

+ HashSet：

  1. `HashSet`中的元素可以是*null*，但只能有一个*null*（因为实现了`Set`接口，所以不允许有重复的值）。
  2. `HashSet`是非线程安全的。
  3. 插入`HashSet`中的对象不保证与插入的顺序一致，元素的排列顺序可能改变。
  4. 向`HashSet`中添加新的对象时，`HashSet`类会进行重复对象元素的判断：判断添加对象和容器内已有对象是否重复，如果重复则不添加，如果不重复则添加。

  > 如果要准确判断`HashSet`中的两个对象重复与否，需要`hashCode()`和`equals()`这两个方法共同来确定，即如果`hashCode()`返回值想等并且`equals()`返回*true*，则判定两个对象重复，只要任一条件不满足，则判定两个对象不重复。

+ `TreeSet`：

  1. `TreeSet`中的元素是一个有序的集合（在插入元素时会进行排序），不允许放入*null*值。
  2. `TreeSet`是非线程安全的。
  3. 向`TreeSet`中添加新的对象时，`TreeSet`会将添加的对象和已有的对象经行比较，存在重复对象则不进行添加，不存在重复对象的情况下，新插入对象和已有对象根据比较结果排序再进行存储。



## 4.`Set`接口的实现类

1. `Set`接口的主要实现类
   + 主要实现类包括`HashSet`、`TreeSet`、`LinkHashSet`、`AbstractSet`等。
2. `HashSet`、`TreeSet`、`LinkHashSet`之间的主要区别
   1. `HashSet`是基于哈希表`HashMap`来实现的，它包含的是不保证有序的不重复的元素。
   2. `TreeSet`是基于`TreeMap`来实现的，而`TreeMap`基于红黑树算法实现，红黑树是一种平衡二叉树，它包含的是有序且不重复的元素。TreeSet支持两种排序方式：自然排序（***Comparable***）和定制排序（***Comparator***）。
   3. `LinkedHashSet`继承自`HashSet`，与`HashSet`相比，他底层是用的双向链表实现，用链表记录数据，实现了按照插入的顺序有序，也就是说，遍历序和插入序是一致的。`LinkedHashSet`在迭代访问`Set`中全部元素时性能会比`HashSet`好，但插入元素时性能不如`HashSet`。
3. `TreeSet`保证有序的方式
   + `TreeSet`底层数据结构是一种自平衡的二叉树，即红黑树，红黑树保证了元素的有序性，无论按照前序、中序、后序都可以有序地读取集合中的元素，也就是说，按照红黑树的节点进行存储和读取数据。



## 5. 输出在字符串中第一次重复出现的字符

```java
public class GetRepeatExample {
    public static void main(String[] args) {
        String s = "hello world";
        char c = getFirstRepeat(s);
        System.out.println("第一次出现重复的字符是：" + c);
    }
    public static char getFirstRepeat(String str) {
        HashSet<Object> set = new HashSet<>();
        int length = str.length();
        char[] chars = str.toCharArray();
        for (int i = 0; i < length; i++) {
            boolean b = set.add(chars[i]);
            if (!b) {
                return chars[i];
            }
        }
        return '0';
    }
}
```



## 6. `ArrayList`、`Vector`和`LinkedList`

1. **ArrayList**
   + `ArrayList`类又称为动态数组，该容器类实现了列表的相关操作。`ArrayList`的内部数据结构由数组实现，因此可对容器内元素实现快速随机访问。但因为在`ArrayList`中插入或删除一个元素需要移动其他元素，而且还存在容量不足时还存在扩容问题，所以不适合在插入和删除操作频繁的场景下使用`ArrayList`。不是线程安全的。
2. **Vector**
   + `Vector`的方法与`ArrayList`的方法的主要差异是增加了`synchronized`关键字，这样保证了执行的线程安全，但也势必会影响`Vector`的性能。所以在不要求线程安全的场景下，建议使用`ArrayList`。
3. **LinkedList**
   + 它的内部数据结构由链表结构实现，并且是非线程安全的，适合数据的动态插入和删除，插入和删除元素时不需要对数据进行移动，所以插入、删除效率较高，但随机访问的速度较慢。



## 7. `ArrayList`和`Vector`的区别

1. 线程安全：`Vector`类是线程安全的，大部分方法都是同步的，而`ArrayList`是非线程安全的。所以`Vector`有较大的系统开销，`ArrayList`在性能上优于`Vector`。
2. 容量扩展机制：当需要扩容时，`ArrayList`和`Vector`都可以进行自动容量扩展。`ArrayList`扩展后数组的大小为原数组长度的1.5倍，同时`ArrayList`可以用构造函数指定数组容量的大小。对于`Vector`，当它的扩展因子大于0时，新数组长度为原数组长度+扩容因子，否则扩展后的数组的大小为原数组的2倍。
3. 类成员属性：`ArrayList`有2个属性，即存储数据的数组`elementData`、存储记录元素个数的`size`。`Vector`有3个属性，即存储数据的数组`elementData`、存储记录元素个数的`size`，同时还有扩展数组大小的扩展因子`capacityIncrement`。



## 8.编程实现去除一个`Vertor`容器中的重复元素

```java
public static Vector<String> getUnique1(Vector<String> vector) {
        Vector<String> strings = new Vector<>();
        for (int i = 0; i < vector.size(); i++) {
            String c = vector.get(i);
            if (!strings.contains(c)) {
                strings.add(c);
            }
        }
        return strings;
    }

    public static Vector<String> getUnique2(Vector<String> vector) {
        HashSet<String> hashSet = new HashSet<>(vector);
        Vector<String> v = new Vector<>();
        v.addAll(hashSet);
        return v;
    }
```

---

>![HashMap和HashTable](imgs\5.png)

## 9.`HashMap`为什么要引入红黑树？

`HashMap`采用数组和链表相结合的数据结构，底层是一个数组，每个数组元素都是一个链表结构，链表的每个节点就是`HashMap`中的每个元素（键值对）。当要向`HashMap`中添加一个键值对时，会先调用该键值对的`key`的`hashCode()`方法计算出`hashCode`值，从而得到该元素在数组中的下标。如果数组在该位置上已保存有元素（已存在一个链表），则说明发生了冲突（不同的`key`值对应了同一个`hash`值，所以映射的数组下标也相同），接下来就要按照`HashMap`冲突管理算法进行处理。

`HashMap`采用链地址法，即用单链表将所有冲突的元素链接起来，通过这种方法来进行冲突管理。但是这个链表并不会无限地增长，当链表中元素个数大于8时，这个链表会自动转换为红黑树结构。之所以引入红黑树结构是因为在链表中查找每个元素的时间复杂度都是`O(n)`，而在红黑树中查找元素的时间复杂度为`O(logn)`，这样当`HashMap`中元素量较多并产生了大量`Hash`冲突时，红黑树的快速增删改查的特点能提高`HashMap`的性能。

>红黑树的三个特点：
>
>1. 根和叶子节点都是黑色的。
>2. 从每个叶子到根的所有路径上不能有两个连续的红色节点。
>3. 从任一节点到它所能到达的叶子节点的所有简单路径都包含相同数目的黑色节点。

### 红黑树结构这么好，为什么在元素个数小于8时还要用链表，而不直接使用红黑树？

当元素数目较少时，链表的效率更高，而红黑树的实现和整体都更复杂，反而会影响整体的性能。















