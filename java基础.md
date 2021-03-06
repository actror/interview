# Java

1. 现在的工作做了一段时间，已经没有太多的激情， 因此希望找到一份更有挑战的工作。然后具体讨论为什么有些厌倦现在的职位了，以及面试的职位我为什么会有兴趣。
2. 尽量避免：___老板太苛刻___ ，___同事太难相处___,___加班太频繁___，___工资太低___。
3. 一个人开口就说现在的工资太低了，希望新工作能加多少多少工资；另一个说我只管努力干活，工资公司看着给，相信公司不会亏待勤奋的员工。



## 1. ` Java` 语言的优势

1. 从语言特性角度，Java语言是一种纯粹的面向对象的编程语言，更能直观地反映现实世界。
2. 其次，Java语言可以“一次编译，到处运行”。只要安装了特定平台的解释器的系统都可以执行Java程序。
3. 从开发角度，Java语言提供了很多功能丰富的内置类库，更利于软件开发。
4. 从安全角度，Java语言具有更高的安全性和健壮性。



## 2. 简述`Java`和`C++` 的相同点和不同点

+ 相同点

1. 二者都是面向对象的语言，都使用面向对象的程序设计思想进行编程，都具有面向对象的基本特征（封装、继承、多态）。

- 不同点

1. Java语言是存粹的面向对象语言，而C++ 不是 。
2. Java是解释性语言，具有平台无关性，而C++ 是编译型语言，是平台相关的。
3. Java和C++ 在技术细节上存在很多差异，而这些差异也决定了Java语言具有更好的安全性，同时代码的维护性更强，也更适合大型系统的开发。
4. Java提供了一些强大的标准库（如：用于数据库访问的`JDBC`库用于实现分布式对象的`IBM`库等），这样可以缩短项目的开发周期，提高开发的效率。



## 3. 如何创建一个不可变类？

1. 类定义为`final`或者把类中的方法定义为`final` ，以保证该类不能被继承和被子类覆盖。
2. 确保所有变量都被`private` 修饰，以保证不被外部访问。
3. 不提供改变成员变量的方法，例如：`setXXX`等方法。
4. 对于类中的非不可变类成员，在使用`getXXX`方法返回该值时，不要直接返回该成员对象本身，而是*clone*该对象并返回对象的拷贝，以保证解除引用关系。基本数据类型成员除外。
5. 通过构造器初始化所有成员，对于非不可变类的成员（一般为引用类型的成员），要通过深拷贝的方法对其初始化，而不能仅做简单的赋值。



## 4. `a++` 和` ++a `的区别

+ 自加运算符`“++”`是单目运算符，当`“++”`出现在操作数左边时表示先做自加运算，然后把自加后的结果放到表达式中进行运算。当`”++“`出现在操作数的右边时表示先把操作数放入表达式中运算，然后把操作数自加1.





## 5. `>>>` 和 `>>` 的区别

+ 无符号右移（`>>>`）它相当于右移运算符（`>>`）而言。对于右移运算符（`>>`），把操作数右移指定位数后，左边空出的位以原来的符号位进行补充。具体来说，如果第一个操作数为正数，则左边补0；如果第一个操作数为负数，则左边补1.



## 6. 说一说 ``&`` 和 `&&` 的区别

+ 在逻辑运算符中，& 是不短路与， && 是短路与。在位运算符中，& 表示按位与。



## 7. 用最有效的方法算出2乘以8等于几

+ 由于位运算符是直接作用于数据上的操作，所以相比较于乘法运算要高效得多。



## 8. ``”==“ ``和 方法``equals ``的区别

+ 运算符`` ”==“ `` 只是用来比较两个变量的值是否相等，也就是用于比较变量所对应的内存中所存储的数值是否想同。``equals``是类的成员方法，一般它是用来比较两个独立对象的内容是否相同（要看具体定义）。如果自定义的类中没有定义``equals``方法，则它将继承``Object``类的``equals``方法，其作用于``”==”``相同。



## 9. 简述在`Java`如何跳出多重循环

+ 使用``break label`` 、``continue label`` 可以跳出多重循环，还可以通过让外层的循环条件表达式的结果受内层循环体代码控制的方法跳出多重循环，或在循环体中使用return 语句等。



## 10. 简述`Java`中如何赋值一个整形数组

1. 使用循环语句将一个数组的内容拷贝到另外一个数组中。

2. 使用数组的`clone()`方法。

3. 应用`System.arraycopy()`方法。

   ```java
   System.arraycopy(Object src, int srcPos, Object dest, int destPos, int length)
   ## src:源数组
   ## srcPos:源数组中的起始位置。
   ## dest: 目标数组
   ## destPos: 目标数据中的起始位置。
   ## length: 要复制的数组元素的数量。
   ```
   
4. 应用`Arrays.copy()`方法.

## 11. `数组`和`String`求长度

+ 数组没有`length()`这个方法，但可以通过`length`属性获取到一个数组的长度。`String`中没有`length`属性，但是有`length()`方法，通过`length()`方法可以获取字符串的长度。



## 12. `String`类型的特征

```java
String s = "Hello";
s = s + "World!";
```

> 原始的`String`对象中的内容到底改变了没有？

+ 原始的`String`对象中的内容并没有发生任何变化，仍然是字符串`“Hello”`,`s`指向了一个新的字符串常量`“Hello World!”` 。

## 13. 简述`String`,`StringBuffer`,`SreingBuilder`的区别和适用场景

+ 当一个字符串需要经常被修改时，需经量避免使用`String`类存储字符串，因为这样会产生一些无用的对象，影响程序的性能。
+ 所以如果在单线程下操作大量数据时应优先使用`StringBulider`;如果在多线程下操作字符串，则应考虑使用`StringBuffer`。



## 14. `final` 块中的代码什么时候会被执行

+ 如果`try`块或`catch`块中有`return`，而`finally`块中没有`return`，则要先执行`finally`块中的代码，然后执行`return`语句。如果`finally`中有`return`语句，那么它会覆盖掉`try`块或`catch`块中的`return`语句。如果在`try`块之前有异常发生，则`finally`块有可能得不到执行。如果直接调用`System.exit(0);`强制退出，则`finally`块也得不到执行。



## 15. 反射机制的基本概念

+ 运用反射机制可以在运行时加载和使用编译期间未知的类型。所谓的Java反射机制，就是在Java程序运行时动态地加载并使用在编译期间并不知道的类。首先，反射机制可以动态获取一个类的信息，包括该类的属性和方法，这个功能可以应用于对class文件进行反编译。其次，反射机制也可以通过类型的名称动态生成对象，并调用对象中的方法。



## 16. 简述反射机制的优缺点

+ 优点： 可以在运行时获取一个类的实例，大大提高了系统的灵活性和可扩展性。
+ 缺点： 性能较差，安全性不高，破坏了类的封装性。



## 17. 简述`final`、`finally`、`finalize`的区别

1. `final`
   + `final`修饰属性时表示该属性不可变；`final`修饰方法时表示该方法不可被覆盖；`final`修饰类时表示该类不可被继承；
2. `finally`
   + 不管`try`块中的代码是否发生异常，也不管哪一个`catch`块得到执行，`finally`块最终总会被执行，所以`finally`块中的代码常被用来执行资源回收、文件流关闭等操作。
3. `finalize`
   + `finalize`是`Object`类的一个方法。在垃圾回收机制执行的时候会调用被回收对象的`finalize`方法。



## 18. 简述`static`的作用

1. `static`成员变量
   + 静态成员变量是属于类的，也就是说，该成员变量并不属于某个对象，即使有多个该类的对象实例，静态成员变量也只有一个。只要静态成员变量所在的类被加载，这个静态成员变量就会被分配内存空间。
2. `static`成员方法
   + `Java`中也支持用`static`关键字修饰的成员方法，即静态成员方法。与此相对应的没有用`static`修饰的成员方法称为非静态成员方法。
   + 于静态成员变量类似，静态成员方法是类方法，它属于类本身而不属于某个对象。因此静态成员方法不需要创建对象就可以被调用，而非静态成员方法则需要通过对象来调用。
   + 特别需要注意的是，在静态成员方法中不能使用`this`、`super`关键字，也不能调用非静态成员方法，同时不能引用非静态成员变量。
3. `static`代码块
   + `static`代码块不需要程序主动调用，在`JVM`加载类时系统会执行`static`代码块，因此在`static`代码块中可以做一些类成员变量的初始化工作。所有的static代码块只能在`JVM`加载类时被执行一次。
4. `static`内部类
   + 在`Java`中还支持用`static`修饰内部类，称为静态内部类。静态成员内部类的特点主要是它本身是类相关的内部类，所以它可以不依赖于外部类实例化而被实例化。



## 19. 简述`volatile`的作用

1. 使用`volatile`关键字会强制将修改的值立即写入主存；
2. 当某个线程修改`volatile`修饰的变量时，会使该变量在任何线程中暂时无效，迫使它从主存中直接读取该值。
3. `volatile`并不能完全替代`synchornized`对线程做互斥。



## 20. 简述`instanceof`的作用

+ `instanceof`关键字的作用是判断一个对象是否是某一个类（或者接口、抽象类、父类）的实例。它的使用方法是 `result = A instanceof B`，其中`A`为某个对象的引用，`B`为某个类的类名（或者接口名、抽象类名、父类名）。其运算结果`result`为一个`boolean`型返回值，如果`A`是`B`的一个实例，则返回`true`；如果`A`不是`B`的一个实例，或者`A`为`null`，则返回`false`。



## 21. 编写程序实现判断 `D:\` 根目录下是否有后缀名为 `.jpg` 的文件，如果有则输出该文件名称

```java
public class FileTest {
    public static void main(String[] args) {
        File file = new File("D:\\");
        File[] listFiles = file.listFiles();
        assert listFiles != null;
        for (File f : listFiles) {
            if (f.getName().endsWith(".jpg")) {
                System.out.println(f.getName());
            }
        }
    }
}
```

>| 方法名                         | 返回类型 | 方法说明                                                     |
>| ------------------------------ | -------- | ------------------------------------------------------------ |
>| `getName()`                    | String   | 获取文件名称                                                 |
>| `canRead()`                    | boolean  | 判断`File`是否可读，可读返回`true`                           |
>| `canWrite()`                   | boolean  | 判断`File`是否可写，可写返回`true`                           |
>| `exists()`                     | boolean  | 判断`File`是否存在，存在返回`true`                           |
>| `length()`                     | long     | 获取`File`长度                                               |
>| `getAbsolutePath()`            | String   | 获取`File`的绝对路径                                         |
>| `getParent()`                  | String   | 获取`File`父目录                                             |
>| `isFile()`                     | boolean  | 判断`File`是否是文件，是文件返回`true`                       |
>| `isDirectory()`                | boolean  | 判断`File`是否是目录，是目录返回`true`                       |
>| `isHidden()`                   | boolean  | 判断`File`是否是隐藏文件，是返回`true`                       |
>| `lastModified()`               | long     | 获取文件最后修改时间，时间是从1970年午夜至最后修改时刻的毫秒数 |
>| `mkdir()`                      | boolean  | 创建目录，如果创建成功则返回`true`，如果目录存在则不创建，并返回`false` |
>| `list()`                       | String[] | 返回目录下的所有文件名                                       |
>| `listFiles()`                  | File[]   | 返回目录下的全部文件对象                                     |
>| `list(FilenameFilter filter)`  | String[] | 返回目录下的所有文件名（`filter`用于指定过滤文件的类型）     |
>| `listFiles(FileFilter filter)` | File[]   | 返回目录下的所有文件对象（`filter`用于指定过滤文件的类型）   |

> `File`类可以新建、删除、重命名一个文件或一个目录，但是File类本身不可以读写文件的内容。要读写文件的内容，需要使用`I/O`流

```java
public class FileTest1 {
    public static void main(String[] args) {
        File file = new File("D:\\");
        JpgFileFilter filter = new JpgFileFilter();
        File[] fileArray = file.listFiles(filter);
        assert fileArray != null;
        for (File f : fileArray) {
            System.out.println(f.getName());
        }
    }
}
class JpgFileFilter implements FileFilter {
    @Override
    public boolean accept(File pathname) {
        if (pathname.isFile() && pathname.getName().endsWith(".jpg")) {
            return true;
        } else {
            return false;
        }

    }
}
```



## 22. 编写程序实现判断`D：\`目录下（包括全部子目录）是否有后缀名为`.jpg`的文件，如果有则输出该文件的名称

```java
public class FileTest2 {
    public static void main(String[] args) {
        File file = new File("D:\\");
        File[] fileArray = file.listFiles();
        FileTest2 ft = new FileTest2();
        ft.listJpgFiles(fileArray);
    }

    public void listJpgFiles(File[] fileArray) {
        if (fileArray == null) {
            return;
        }
        for (File f : fileArray) {
            if (f.isFile()) {
                if (f.getName().endsWith(".jpg")) {
                    System.out.println(f.getName());
                }
            }
            if (f.isDirectory()) {
                listJpgFiles(f.listFiles());
            }
        }
    }
}
```



## 23. 简述`Java`的`I/O`流的分类

1. 按照流的方向划分

   + 输入流：可将数据从外部设备（文件、磁盘、网络等）读到内存中。
   + 输出流：可将内存中的数据写到外部设备（文件、磁盘、网络等）中。

2. 按照以处理数据类型划分

   + 字节流：以字节为单位的流，可操作的最小数据单元为`8bits`的字节。字节流包含两个抽象基类——`InputStream`（输入流）`OutputStream`（输出流），不同输入输出源的字节流类型都是派生自这两个基类。
   + 字符流：以字符为单位的流，可操作的最小数据单元为`16bits`的字符。字符流包含两个抽象基类——``Reader`（输入流）和`Writer`（输出流），不同输入输出源的字符流类型都是派生自这两个基类。

3. 按照流的角色划分

   + 节点流：它是从/向某个特定设定`IO`设备读取\写入数据的流，处于数据处理的下层，因此也被称为低级流。
   + 处理流：用于对一个已存在的流进行封装，一般包装节点流。因此处理流通常也被称为高级流。
+ ![I/O流的框架体系](imgs/1.png)
+ ![流的Java类关系](imgs/2.png)



## 24. 编写一段程序可以在屏幕上打印出这段程序的源代码

```java
public class FileTest3 {
    public static void main(String[] args) throws IOException {
        FileInputStream fis = new FileInputStream("./src/com/hang/IO/File/FileTest3.java");
        byte[] bytes = new byte[1024];
        int hasRead = 0;
        while ((hasRead = fis.read(bytes)) > 0) {
            System.out.println(new String(bytes, 0, hasRead));
        }
        fis.close();
    }
}
```



## 25. 什么是对象的序列化和反序列化

在Java中如果一个类实现了Serializable接口则表明该类是可序列化的。需要注意的是，Serializeable接口只是一个标记接口，实现该接口无需实现任何方法，它只表现实现该接口的类的对象可被序列化。为该类提供一个全局常量serialVersionUID。

### 1.序列化

1. 使用一个节点流（一般是输出流，例如FileOutputStream）对象构建一个处理流ObjectOutputStream对象。
2. 调用ObjectOutputStream对象的writeObject(object)方法将对象object序列化，并输出到ObjectOutputStream对象指定的流中。

### 2.反序列化

1. 使用一个节点流（一般是输入流，例如FileInputStream）对象构建一个处理流ObjectInputStream对象。
2. 调用ObjectInputStream对象的readObject()方法读取流中的对象，该方法会返回一个Object类型的对象，可将该对象强制类型转换成其真实的类型。





