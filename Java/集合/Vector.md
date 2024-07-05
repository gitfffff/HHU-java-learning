# Vector 介绍

`Vector` 是 Java 集合框架（Java Collections Framework）中的一个类，它实现了 `List` 接口，是一个动态数组。与普通的数组相比，`Vector` 提供了更多的功能和灵活性，如动态扩展大小、线程安全等。然而，由于线程安全性的开销，`Vector` 的性能通常不如非线程安全的 `ArrayList`。
==省流：从使用方法的角度来看，`Vector` 和 `ArrayList` 在 Java 中的很多操作是相似的（几乎一模一样，如果你会了ArrayList，Vector可以不单独学），因为两者都实现了 `List` 接口。==
## 基本特性

- **动态扩展**：当添加元素导致当前容量不足时，`Vector` 会自动扩展其内部数组的大小。
- **线程安全**：多个线程可以同时访问和修改 `Vector`，而不需要额外的同步机制。但这也带来了性能上的开销。
- **有序**：`Vector` 维护了元素的插入顺序。
- **允许重复元素**：与 `Set` 不同，`Vector` 允许存储重复的元素。

## 构造方法

`Vector` 类提供了几个构造方法，用于创建新的 `Vector` 实例：

| 构造方法 | 描述 |
| --- | --- |
| `Vector()` | 创建一个空的 `Vector` 实例，其初始容量为 10。 |
| `Vector(int initialCapacity)` | 创建一个空的 `Vector` 实例，其初始容量由参数指定。 |
| `Vector(int initialCapacity, int capacityIncrement)` | 创建一个空的 `Vector` 实例，其初始容量由 `initialCapacity` 参数指定，并且当需要扩展容量时，将增加 `capacityIncrement` 大小。 |
| `Vector(Collection<? extends E> c)` | 创建一个包含指定集合中所有元素的 `Vector` 实例。 |

## 常用方法

`Vector` 类提供了许多方法来操作元素，包括添加、删除、查找等：

- `add(E e)`：将指定元素添加到向量的末尾。
- `add(int index, E element)`：在指定位置插入指定元素。
- `addAll(Collection<? extends E> c)`：将指定集合中的所有元素添加到向量的末尾。
- `addAll(int index, Collection<? extends E> c)`：从指定位置开始，将指定集合中的所有元素插入到此向量中。
- `remove(int index)`：移除指定位置的元素。
- `remove(Object o)`：移除指定元素（如果存在）。
- `get(int index)`：返回指定位置的元素。
- `size()`：返回向量中的元素数量。
- `isEmpty()`：检查向量是否为空。
- `clear()`：移除向量中的所有元素。

此外，`Vector` 还提供了许多其他方法，如用于查找元素的 `indexOf` 和 `lastIndexOf`，以及用于修改元素的 `setElementAt` 等。

## 示例

这个示例创建了一个 `Vector` 实例，并演示了如何添加、访问、插入、遍历和移除元素。

```java
import java.util.Vector;

public class VectorExample {
    public static void main(String[] args) {
        // 创建一个空的 Vector 实例
        Vector<String> vector = new Vector<>();

        // 添加元素
        vector.add("Apple");
        vector.add("Banana");
        vector.add("Cherry");

        // 访问元素
        System.out.println(vector.get(1)); // 输出 "Banana"

        // 插入元素
        vector.add(1, "Blueberry");

        // 遍历元素
        for (String fruit : vector) {
            System.out.println(fruit);
        }

        // 移除元素
        vector.remove("Banana");

        // 再次遍历元素
        for (String fruit : vector) {
            System.out.println(fruit);
        }
    }
}
```
