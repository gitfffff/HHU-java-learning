```java
//使用List集合存储10个学生信息。  
      //  学生信息：姓名，年龄，成绩。   //    统计所有姓“张”的同学的平均成绩import java.util.ArrayList;  
 class Student3 {  
    String name;  
    int age;  
    int score;  
    public Student3(String name, int age, int score){  
        this.name=name;  
        this.age=age;  
        this.score=score;  
    }  
}  
public class MyListDemo {  
    public static void main(String[] args) {  
        ArrayList<Student3> list=new ArrayList<>();  
        list.add(new Student3("张三",18,90));  
        //这里要注意类对象要new出来，进行类型转化  
        list.add(new Student3("李四",19,80));  
        list.add(new Student3("张五",20,85));  
        list.add(new Student3("张六",21,95));  
        list.add(new Student3("李七",22,75));  
        int score=0;  
        int count=0;  
        for (Student3 s:list){  
            if(s.name.startsWith("张")){  
                score+=s.score;  
                count++;  
            }  
        }  
        System.out.println("所有姓“张”的同学的平均成绩为："+score/count);  
    }  
}
```

```java
//模拟HashSet
package com.example.simulate;  
  
public class Person {  
    private String name;  
    int age;  
    String gender;  
  
    public Person(String name, int age) {  
        // 构造函数  
        this.name = name;  
        this.age = age;  
    }  
  
    public String toString() {  
        return "name: " + name + " age: " + age;  
    }  
  
    public int hashCode() {  
        return name.hashCode() +7*age;  
    }  
  
    public boolean equals(Object obj) {  
        if (obj instanceof Person) {  
            Person p = (Person) obj;  
            return p.age == age && p.name.equals(name);  
        }  
        return false;  
    }  
}
package com.example.simulate;  
import java.util.ArrayList;  
public class Demo {  
    public static void main(String[] args) {  
        ArrayList<Person> arr = new ArrayList<>();  
        Person p1 = new Person("jack", 20);  
        Person p2 = new Person("rose", 18);  
        Person p3 = new Person("rose", 18);  
        arr.add(p1);  
        arr.add(p2);  
        arr.add(p3);  
        ArrayList<Person> arr2 = new ArrayList<>();  
        for (Person per : arr) {  
            if(!arr2.contains(per)){  
                arr2.add(per);  
            }  
        }  
      System.out.println(arr2);  
}}
```