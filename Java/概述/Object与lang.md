# Object
在Java中，`Object` 类是所有类的根类。换句话说，Java中的每一个类都直接或间接地继承了 `Object` 类。`Object` 类定义了一些基本的方法，这些方法可以被所有的Java对象使用。

以下是 `Object` 类的一些主要特点和常用方法：

 特点：

1. **根类**：`Object` 类是Java类层次结构中的根类，所有的类都直接或间接地继承自它。
    
2. **默认方法**：`Object` 类定义了一些方法，这些方法为所有Java对象提供了基本的行为。

| 方法名                             | 描述                                                                                       |
| ------------------------------- | ---------------------------------------------------------------------------------------- |
| `toString()`                    | 返回对象的字符串表示。==默认实现返回类名和对象的哈希码的无意义字符串==，但通常==建议子类重写此方法以返回有意义的描述==。                         |
| ==equals(Object obj)==          | 比较此对象与指定对象是否相等。==默认实现是比较对象的内存地址（即判断两个对象是否是同一个对象的引用）。子类通常重写此方法以提供基于对象内容的比较。==             |
| `hashCode()`                    | 返回该对象的哈希码值。通常与哈希表（如`HashMap`、`HashSet`）一起使用。当重写`equals(Object obj)`方法时，通常也需要重写此方法以保持一致性。 |
| ==clone()==                     | 创建并返回此对象的一个副本。默认实现是保护方法，子类需要实现`Cloneable`接口才能调用此方法，否则将抛出`CloneNotSupportedException`异常。  |
| `finalize()`                    | 当垃圾回收器确定不存在对该对象的更多引用时，在对象被垃圾回收之前调用此方法。现代Java虚拟机已经很少使用此方法，且其行为可能因实现而异。                    |
| `getClass()`                    | 返回一个表示此`Object`运行类`Class`的`Class`对象。                                                     |
| `notify()`                      | 唤醒在此对象监视器上等待的单个线程。只有当前线程是此对象监视器的所有者时，才能调用此方法。                                            |
| `notifyAll()`                   | 唤醒在此对象监视器上等待的所有线程。只有当前线程是此对象监视器的所有者时，才能调用此方法。                                            |
| `wait(long timeout)`            | 使当前线程等待（即暂停执行）直到其他线程调用此对象的`notify()`方法或`notifyAll()`方法，或者超过指定的时间量。当前线程必须拥有此对象监视器的所有权。    |
| `wait(long timeout, int nanos)` | 与`wait(long timeout)`类似，但增加了纳秒级精度的时间量。                                                   |
| `wait()`                        | 使当前线程等待（即暂停执行）直到其他线程调用此对象的`notify()`方法或`notifyAll()`方法。当前线程必须拥有此对象监视器的所有权。               |
注意：`wait()`、`notify()` 和 `notifyAll()` 方法通常与 `synchronized` 关键字一起使用，以在多线程环境中控制对共享资源的访问。这些方法必须在同步块或同步方法内调用，否则将抛出 `IllegalMonitorStateException` 异常。
# lang
`java.lang`包是Java编程语言的核心包之一，它包含了Java程序所需的基本类和接口。以下是一些`java.lang`包中的常用类及其简要介绍：

| 类名                                                                              | 描述                                                                                                                    |
| ------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| `Object`                                                                        | Java 中所有类的根类，提供了基本的方法如 `equals()`, `hashCode()`, `toString()`, `getClass()`, `notify()`, `notifyAll()`, 和 `wait()` 等。 |
| `Byte`, `Short`, ==Integer==, `Long`, `Float`, `Double`, `Character`, `Boolean` | 基本数据类型的包装类，提供了将基本数据类型转换为对象类型（自动装箱）和将对象类型转换为基本数据类型（自动拆箱）的功能。                                                           |
| `String`                                                                        | 用于处理字符串（文本）数据，提供了一系列方法来操作字符串，如连接、比较、查找、替换等。                                                                           |
| `StringBuffer`                                                                  | 用于在内存中构建和修改字符串，是可变的（mutable），提供了类似于 `String` 类的方法。                                                                    |
| `StringBuilder`                                                                 | 与 `StringBuffer` 类似，但非线程安全，因此在单线程环境中通常更快。                                                                             |
| `Math`                                                                          | 提供了一系列静态方法来进行数学计算，如三角函数、指数函数、对数函数、平方根等。                                                                               |
| `System`                                                                        | 提供了一些与系统交互的方法，如访问系统属性、输入/输出流等。                                                                                        |
| `Class`                                                                         | 代表类的运行时类（class-object），提供了在运行时获取类的信息（如类名、方法、字段等）的功能。                                                                  |
| `Throwable`（及其子类 `Error` 和 `Exception`）                                         | 代表 Java 中的错误和异常，是所有错误和异常类的超类，提供了处理错误和异常的方法。                                                                           |
| `Process`                                                                       | 提供与本地进程的交互功能。                                                                                                         |
| `Runtime`                                                                       | 表示 Java 应用程序的运行时环境，允许应用程序与其运行的环境进行交互。                                                                                 |
| `SecurityManager`                                                               | 允许应用程序实现安全管理策略。                                                                                                       |
| ==Thread==                                                                      | Thread类提供了创建和操作线程的基本方法，包括线程的启动（通过start()方法）、获取线程的ID、名称、优先级和状态等。                                                       |

请注意，这个列表并不完整，但包含了 `java.lang` 包中一些最常用的类。
总的来说，`java.lang`包中的类为Java程序提供了基本的数据类型、字符串处理、数学计算、系统交互和错误处理等功能，是Java编程中不可或缺的一部分。