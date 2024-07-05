在 Java 编程中，"Comparable" 是一个接口，它允许类的实例之间进行自然排序。

- **定义**：
    - `Comparable` 是 Java 标准库中的一个接口，它包含一个名为 `compareTo` 的方法。
- **使用**：
    - 当一个类实现了 `Comparable` 接口，并提供了 `compareTo` 方法的实现时，这个类的实例就可以使用 `Collections.sort()` 或 `Arrays.sort()` 等方法进行排序。
    - `compareTo` 方法应该根据类的自然排序顺序来比较两个对象。
- **方法签名**：
    - `public int compareTo(T o);`
        - 其中 `T` 是实现了 `Comparable` 接口的类的类型。
        - 这个方法应该返回一个整数，根据以下规则：
            - 如果当前对象小于、等于或大于指定的对象，则分别返回负整数、零或正整数。
- **示例**：
    - 假设有一个 `Student` 类，该类包含学生的姓名和分数。如果我们想根据分数对学生进行排序，我们可以让 `Student` 类实现 `Comparable<Student>` 接口，并在其中提供 `compareTo` 方法的实现。
    在Java中，`Comparable`接口通常用于实现对象的自然排序。以下是一个简单的例子，演示了如何为一个`Student`类实现`Comparable`接口，以便根据分数进行排序：

```java
public class Student implements Comparable<Student> {
    private String name;
    private int score;

    public Student(String name, int score) {
        this.name = name;
        this.score = score;
    }

    // Getter 和 Setter 方法（省略）

    // 实现 Comparable 接口的 compareTo 方法
    @Override
    public int compareTo(Student other) {
        // 按照分数进行升序排序
        // 如果当前对象的分数小于另一个对象的分数，返回负数
        // 如果分数相等，返回0
        // 如果当前对象的分数大于另一个对象的分数，返回正数
        return this.score - other.score;
    }

    // toString 方法（用于输出）
    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", score=" + score +
                '}';
    }

    // 主函数，用于演示排序
    public static void main(String[] args) {
        // 创建一个学生列表
        List<Student> students = new ArrayList<>();
        students.add(new Student("Alice", 85));
        students.add(new Student("Bob", 92));
        students.add(new Student("Charlie", 78));

        // 使用 Collections.sort 进行排序
        Collections.sort(students);

        // 输出排序后的学生列表
        for (Student student : students) {
            System.out.println(student);
        }
    }
}
```

在这个例子中，`Student`类实现了`Comparable<Student>`接口，并覆盖了`compareTo`方法。`compareTo`方法比较两个`Student`对象的分数，并返回一个整数来表示它们之间的顺序关系。在`main`方法中，我们创建了一个`Student`对象的列表，并使用`Collections.sort`方法对其进行排序。由于`Student`类实现了`Comparable`接口，`Collections.sort`能够知道如何根据分数对`Student`对象进行排序。最后，我们遍历排序后的列表并打印每个学生的信息。