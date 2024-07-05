## Iterator
Iterator 是 Java 的 java.util 包中的一个接口
iterator() 是 Java 集合框架中的一个方法，它返回一个 Iterator 对象，该对象可以用来遍历集合中的元素
Iterator确实是一个接口，你不能直接实例化一个接口。但是，你可以获取一个实现了Iterator接口的对象。这通常是通过调用一个集合的iterator()方法来完成的。  在你的代码中，`Iterator<Student3> it=list.iterator();`这行代码做的就是这个。list.iterator()方法返回一个Iterator对象，这个对象是ArrayList类的一个内部类实例，这个内部类实现了Iterator接口。  所以，虽然你不能直接实例化Iterator接口，但你可以通过调用某些方法（如iterator()）来获取实现了Iterator接口的对象，然后使用这个对象来遍历集合。
`Iterator` 是 Java 集合框架中用于遍历集合元素的一个接口。以下是 `Iterator` 接口中常用方法的表格表示：



| 方法          | 描述                                                                                                                                                                                          |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `hasNext()` | 检查是否还有下一个元素可以迭代。如果有，返回 `true`；否则返回 `false`。                                                                                                                                                 |
| `next()`    | ==返回迭代中的下一个元素。==在第一次调用之前，应调用 `hasNext()` 来确保还有下一个元素。如果已到达集合末尾，再次调用此方法将抛出 `NoSuchElementException`。                                                                                          |
| `remove()`  | 从迭代器最后返回的元素（即最近一次调用 `next()` 方法的元素）所在的集合中移除它。在调用 `remove()` 之前，必须先调用 `next()`。否则，将抛出 `IllegalStateException`。此外，并非所有的迭代器实现都支持 `remove()` 操作，如果不支持，调用此方法将抛出 `UnsupportedOperationException`。 |
|             |                                                                                                                                                                                             |

需要注意的是，`Iterator` 本身并不包含集合元素，它只是一个用于遍历集合的接口。在实际使用中，你会通过集合对象（如 `List`、`Set`）的 `iterator()` 方法来获取一个 `Iterator` 对象，然后使用该对象来遍历集合中的元素。

此外，虽然 `Iterator` 在 Java 集合框架中非常常用，但在并发环境下使用时需要特别注意线程安全问题。如果需要在多线程环境中安全地遍历集合，可以考虑使用并发集合（如 `ConcurrentHashMap`）或在使用迭代器时加上适当的同步措施。

> [!tip] 注意
> 每写一次`next()`就相当于调用一次，意味着跳过一个对象
```java
public class MyListDemo {
    public static void main(String[] args) {
        ArrayList<Student3> list = new ArrayList<>();
        list.add(new Student3("张三", 18, 90));
        list.add(new Student3("李四", 19, 80));
        list.add(new Student3("张五", 20, 85));
        list.add(new Student3("张六", 21, 95));
        list.add(new Student3("李七", 22, 75));
        int score = 0;
        int count = 0;
        Iterator<Student3> it = list.iterator();
        while (it.hasNext()) {
            Student3 student = it.next();
            //这里一定一定要注意
            if (student.name.startsWith("张")) {
                score += student.score;
                count++;
            }
        }
        if (count != 0) {
            System.out.println("所有姓“张”的同学的平均成绩为：" + score / count);
        } else {
            System.out.println("没有姓“张”的同学。");
        }
    }
}
```
## `ListIterator` 
是 Java 集合框架中的一个接口，它允许程序员在列表（如 `ArrayList`、`LinkedList` 等）中双向遍历，同时支持元素的添加和删除操作。由于 `ListIterator` 是一个接口，它并没有直接的“表格”表示，但我可以为你描述其主要的方法和属性，以表格的形式呈现。

`ListIterator`获取方法的详细说明：

1. **listIterator()方法**：
    - 此方法返回列表（List）的列表迭代器（从头到尾）。
    - 示例：`ListIterator<String> iterator = list.listIterator();`
2. **==listIterator(int index)方法==**：
    - ==此方法返回列表（List）中指定位置的列表迭代器==。索引指定了迭代器首次调用`next`方法时的元素位置，或者首次调用`previous`方法时的前一个元素位置。
    - 示例：`ListIterator<String> iterator = list.listIterator(2);` 这里，迭代器将从索引为2的元素开始。

| 方法 | 描述 |
| --- | --- |
| `boolean hasNext()` | 如果列表迭代器有多个元素，则返回 `true`（在正向遍历列表中时）。 |
| `E next()` | 返回列表中的下一个元素，并将迭代器位置向前移动一个位置。 |
| `boolean hasPrevious()` | 如果列表迭代器在反向遍历列表时有多个元素，则返回 `true`。 |
| `E previous()` | 返回列表中的前一个元素，并将迭代器位置向后移动一个位置。 |
| `int nextIndex()` | 返回对 `next` 的后续调用将返回的元素的索引（在正向遍历列表中时）。 |
| `int previousIndex()` | 返回对 `previous` 的后续调用将返回的元素的索引（在反向遍历列表中时）。 |
| `void remove()` | 从列表中删除上次 `next` 或 `previous` 访问的元素（可选操作）。 |
| `void set(E e)` | 用指定的元素替换上次 `next` 或 `previous` 访问的元素（可选操作）。 |
| `void add(E e)` | 将指定的元素插入列表（可选操作）。该元素将插入到 `next` 或 `previous` 最后一次访问的位置。 |

注意：

* `ListIterator` 的 `remove`、`set` 和 `add` 方法都是可选操作，这意味着并非所有的 `ListIterator` 实现都必须支持它们。例如，一个只读的 `ListIterator` 可能会抛出 `UnsupportedOperationException` 如果调用了这些方法。
* `ListIterator` 通常通过调用列表的 `ListIterator<E> listIterator()` 或 `ListIterator<E> listIterator(int index)` 方法获得。
