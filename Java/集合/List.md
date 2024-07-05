## 2.List集合

### 2.1List集合的概述和特点【记忆】

- List集合的概述
  - 有序集合,==这里的有序指的是存取顺序==
  - 用户可以精确控制列表中每个元素的插入位置,用户可以==通过整数索引访问元素==,并搜索列表中的元素
  - 与Set集合不同,列表通常==允许重复的元素==
- List集合的特点
  - 存取有序
  - 可以重复
  - 有索引

### 2.2List集合的特有方法【应用】

- 方法介绍

| 方法名                              | 描述                  |
| -------------------------------- | ------------------- |
| `void add(int index, E element)` | 在此集合中的指定位置插入指定的元素   |
| `E remove(int index)`            | 删除指定索引处的元素，返回被删除的元素 |
| `E set(int index, E element)`    | 修改指定索引处的元素，返回被修改的元素 |

- 示例代码
  
  ```java
  public class MyListDemo {
      public static void main(String[] args) {
          List<String> list = new ArrayList<>();
          list.add("aaa");
          list.add("bbb");
          list.add("ccc");
          //method1(list);
          //method2(list);
          //method3(list);
          //method4(list);
      }
  
      private static void method4(List<String> list) {
          //        E get(int index)        返回指定索引处的元素
          String s = list.get(0);
          System.out.println(s);
      }
  
      private static void method3(List<String> list) {
          //        E set(int index,E element)    修改指定索引处的元素，返回被修改的元素
          //被替换的那个元素,在集合中就不存在了.
          String result = list.set(0, "qqq");
          System.out.println(result);
          System.out.println(list);
      }
  
      private static void method2(List<String> list) {
          //        E remove(int index)        删除指定索引处的元素，返回被删除的元素
          //在List集合中有两个删除的方法
          //第一个 删除指定的元素,返回值表示当前元素是否删除成功
          //第二个 删除指定索引的元素,返回值表示实际删除的元素
          String s = list.remove(0);
          System.out.println(s);
          System.out.println(list);
      }
  
      private static void method1(List<String> list) {
          //        void add(int index,E element)    在此集合中的指定位置插入指定的元素
          //原来位置上的元素往后挪一个索引.
          list.add(0,"qqq");
          System.out.println(list);
      }
  }
  ```

### 2.3List集合的五种遍历方式【应用】

1. 迭代器
2. 列表迭代器
3. 增强for
4. Lambda表达式
5. 普通for循环

代码示例：

```java
//创建集合并添加元素
List<String> list = new ArrayList<>();
list.add("aaa");
list.add("bbb");
list.add("ccc");

//1.迭代器
/*Iterator<String> it = list.iterator();
     while(it.hasNext()){
        String str = it.next();
        System.out.println(str);
}*/


//2.增强for
//下面的变量s，其实就是一个第三方的变量而已。
//在循环的过程中，依次表示集合中的每一个元素
/* for (String s : list) {
       System.out.println(s);
   }*/

//3.Lambda表达式
//forEach方法的底层其实就是一个循环遍历，依次得到集合中的每一个元素
//并把每一个元素传递给下面的accept方法
//accept方法的形参s，依次表示集合中的每一个元素
//list.forEach(s->System.out.println(s) );


//4.普通for循环
//size方法跟get方法还有循环结合的方式，利用索引获取到集合中的每一个元素
/*for (int i = 0; i < list.size(); i++) {
            //i:依次表示集合中的每一个索引
            String s = list.get(i);
            System.out.println(s);
        }*/

// 5.列表迭代器
//获取一个列表迭代器的对象，里面的指针默认也是指向0索引的

//额外添加了一个方法：在遍历的过程中，可以添加元素
ListIterator<String> it = list.listIterator();
while(it.hasNext()){
    String str = it.next();
    if("bbb".equals(str)){
        //qqq
        it.add("qqq");
    }
}
System.out.println(list);
```

### 2.4 细节点注意：

List系列集合中的两个删除的方法

```java
1.直接删除元素
2.通过索引进行删除
```

代码示例:

```java
//List系列集合中的两个删除的方法
//1.直接删除元素
//2.通过索引进行删除

//1.创建集合并添加元素
List<Integer> list = new ArrayList<>();

list.add(1);
list.add(2);
list.add(3);


//2.删除元素
//请问：此时删除的是1这个元素，还是1索引上的元素？
//为什么？
//因为在调用方法的时候，如果方法出现了重载现象
//优先调用，实参跟形参类型一致的那个方法。

//list.remove(1);


//手动装箱，手动把基本数据类型的1，变成Integer类型
Integer i = Integer.valueOf(1);

list.remove(i);

System.out.println(list);

```

## 3.数据结构

### 3.1数据结构之栈和队列【记忆】

- 栈结构
  ​    先进后出

- 队列结构
  ​    先进先出

### 3.2数据结构之数组和链表【记忆】

- 数组结构
  ​    查询快、增删慢

- 队列结构
  ​    查询慢、增删快

## 4.List集合的实现类

### 4.1List集合子类的特点【记忆】

- ArrayList集合
  ​    底层是数组结构实现，查询快、增删慢

- LinkedList集合
  ​    底层是链表结构实现，查询慢、增删快

### 4.2LinkedList集合的特有功能【应用】

- 特有方法
  
  | 方法名                       | 说明               |
  | ------------------------- | ---------------- |
  | public void addFirst(E e) | 在该列表开头插入指定的元素    |
  | public void addLast(E e)  | 将指定的元素追加到此列表的末尾  |
  | public E getFirst()       | 返回此列表中的第一个元素     |
  | public   E getLast()      | 返回此列表中的最后一个元素    |
  | public E removeFirst()    | 从此列表中删除并返回第一个元素  |
  | public   E removeLast()   | 从此列表中删除并返回最后一个元素 |

- 示例代码
  
  ```java
  public class MyLinkedListDemo4 {
      public static void main(String[] args) {
          LinkedList<String> list = new LinkedList<>();
          list.add("aaa");
          list.add("bbb");
          list.add("ccc");
  //        public void addFirst(E e)    在该列表开头插入指定的元素
          //method1(list);
  
  //        public void addLast(E e)    将指定的元素追加到此列表的末尾
          //method2(list);
  
  //        public E getFirst()        返回此列表中的第一个元素
  //        public E getLast()        返回此列表中的最后一个元素
          //method3(list);
  
  //        public E removeFirst()        从此列表中删除并返回第一个元素
  //        public E removeLast()        从此列表中删除并返回最后一个元素
          //method4(list);
  
      }
  
      private static void method4(LinkedList<String> list) {
          String first = list.removeFirst();
          System.out.println(first);
  
          String last = list.removeLast();
          System.out.println(last);
  
          System.out.println(list);
      }
  
      private static void method3(LinkedList<String> list) {
          String first = list.getFirst();
          String last = list.getLast();
          System.out.println(first);
          System.out.println(last);
      }
  
      private static void method2(LinkedList<String> list) {
          list.addLast("www");
          System.out.println(list);
      }
  
      private static void method1(LinkedList<String> list) {
          list.addFirst("qqq");
          System.out.println(list);
      }
  }
  ```

## 5. 源码分析

### 5.1 ArrayList源码分析：

核心步骤：

1. 创建ArrayList对象的时候，他在底层先创建了一个长度为0的数组。
   数组名字：elementDate，定义变量size。
   size这个变量有两层含义：
   ①：元素的个数，也就是集合的长度
   ②：下一个元素的存入位置

2. 添加元素，添加完毕后，size++

扩容时机一：

3. 当存满时候，会创建一个新的数组，新数组的长度，是原来的1.5倍，也就是长度为15.再把所有的元素，全拷贝到新数组中。如果继续添加数据，这个长度为15的数组也满了，那么下次还会继续扩容，还是1.5倍。

扩容时机二：

4. 一次性添加多个数据，扩容1.5倍不够，怎么办呀？
   如果一次添加多个元素，1.5倍放不下，那么新创建数组的长度以实际为准。

举个例子：
在一开始，如果默认的长度为10的数组已经装满了，在装满的情况下，我一次性要添加100个数据很显然，10扩容1.5倍，变成15，还是不够，

怎么办？

此时新数组的长度，就以实际情况为准，就是110

具体分析过程可以参见视频讲解。

**添加一个元素时的扩容：**

![第一次添加数据](img\第一次添加数据.png)

**添加多个元素时的扩容：**

![第11次添加数据](img\第11次添加数据.png)

### 5.2 LinkedList源码分析：

底层是双向链表结构

核心步骤如下：

1. 刚开始创建的时候，底层创建了两个变量：一个记录头结点first，一个记录尾结点last，默认为null
2. 添加第一个元素时，底层创建一个结点对象，first和last都记录这个结点的地址值
3. 添加第二个元素时，底层创建一个结点对象，第一个结点会记录第二个结点的地址值，last会记录新结点的地址值

具体分析过程可以参见视频讲解。

![LinkedList源码分析](img\LinkedList源码分析.png)

### 5.3 迭代器源码分析：

迭代器遍历相关的三个方法：

* Iterator<E> iterator()  ：获取一个迭代器对象

* boolean hasNext()       ：判断当前指向的位置是否有元素

* E next()                ：获取当前指向的元素并移动指针

![迭代器源码分析](/C:\Users\W\Desktop\Hohai\黑马\入门到起飞（下）\资料\day22-集合（List集合）\笔记\笔记/img\迭代器源码分析.png)
