
### 构造函数

| 构造函数 | 描述 |
| --- | --- |
| `Character(char value)` | 使用指定的 `char` 值创建一个 `Character` 对象。 |

### 访问器

| 访问器 | 描述 |
| --- | --- |
| `charValue()` | 返回此 `Character` 对象的 `char` 值。 |

### 比较

| 比较方法 | 描述 |
| --- | --- |
| `compareTo(Character anotherCharacter)` | 按字典顺序将此 `Character` 对象与指定的 `Character` 对象进行比较。 |

### 相等性

| 相等性方法 | 描述 |
| --- | --- |
| `equals(Object obj)` | 将此对象与指定对象进行比较以确定它们是否相等。 |

### 测试

| 测试方法 | 描述 |
| --- | --- |
| `isDigit(char ch)` | 判断指定的 `char` 值是否是一个数字。 |
| `isLetter(char ch)` | 判断指定的 `char` 值是否是一个字母。 |
| `isLetterOrDigit(char ch)` | 判断指定的 `char` 值是否是一个字母或数字。 |
| `isWhitespace(char ch)` | 判断指定的 `char` 值是否是一个空白字符（空格、制表符、换页符等）。 |
| `isDefined(char ch)` | 判断指定的 `char` 值是否是一个 Unicode 定义的字符。 |
| `isLowerCase(char ch)` | 判断指定的 `char` 值是否是一个小写字母。 |
| `isUpperCase(char ch)` | 判断指定的 `char` 值是否是一个大写字母。 |
| `isISOControl(char ch)` | 判断指定的 `char` 值是否是一个 ISO 控制字符。 |
| `isMirrored(char ch)` | 判断指定的 `char` 值是否是一个镜像字符。 |

### 转换

| 转换方法 | 描述 |
| --- | --- |
| `toLowerCase(char ch)` | 将指定的 `char` 值转换为小写（如果它是一个大写字母的话）。 |
| `toUpperCase(char ch)` | 将指定的 `char` 值转换为大写（如果它是一个小写字母的话）。 |
| `forDigit(int digit, int radix)` | 将指定的十进制整数转换为其对应的字符表示形式，用于指定的基数。 |
| `digit(char ch, int radix)` | 将指定的字符转换为指定基数的数字。 |

### 其他

| 其他方法         | 描述                            |
| ------------ | ----------------------------- |
| `hashCode()` | 返回此 `Character` 对象的哈希码值。      |
| `toString()` | 返回表示此 `Character` 对象的值的字符串。   |
| `TYPE`       | 表示 `Character` 类的 `Class` 对象。 |
实例
```java
class Vert{  
    public static String vert(String s){  
        StringBuffer  s1= new StringBuffer();  
        char ch;  
        for (int i = 0; i < s.length(); i++) {  
            ch = s.charAt(i);  
            if (Character.isLetter(ch)){  
                s1.append(Character.toLowerCase(ch));  
            }  
        }  
        return s1.toString();  
    }  
}  
public class SystemDemo {  
    public static void main(String[] args) {  
        String s = "hel1lo1Wo2rL1D";  
        System.out.println(Vert.vert(s));  
    }  
}
```