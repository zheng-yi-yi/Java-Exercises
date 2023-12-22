# Java-Exercises
🚀🚀🚀我的Java练习题仓库！

## 目录

- Java-Exercise
  - [基础语法和数据类型](#基础语法和数据类型)
  - [面向对象编程（OOP）](#面向对象编程oop)
  - [异常处理](#异常处理)
  - [集合框架](#集合框架)
  - [输入输出操作](#输入输出操作)
  - [数据结构与算法](#数据结构与算法)
  - [多线程](#多线程)
  - [网络编程](#网络编程)
  - [数据库连接](#数据库连接)
  - [Lambda表达式和流](#lambda表达式和流)
  - [设计模式](#设计模式)
  - [Java 8新特性](#java-8新特性)


## 基础语法和数据类型

【单选题】给定代码：

```java
public class SwitchTest{
    public static void main(String[] args) {
        System.out.println("value="+switchit(4));   // 输出？
    }
    public static int switchit(int x) {
        int j=1;
        switch (x) {
        case 1:j++;
        case 2:j++;
        case 3:j++;
        case 4:j++;
        case 5:j++;
        default:j++;
        }
        return j+x;
    }
}
```

请问第三行将输出什么？

A、value=6

B、value=8

C、value=3

D、value=5

E、value=4

<details>
<summary>查看答案</summary>

### 正确答案：B

没有`break`，从`case 4`开始一直执行到最后，`j`自加`3`次变成了`4`,结果返回`8`。

</details>

---

【单选题】以下哪个选项是编译和执行上述代码片段的结果？

```java
public class Main {
    public static void main(String[] args) {
        Boolean flag = false;
        if (flag = true) {
            System.out.println("true");
        } else {
            System.out.println("false");
        }
    }
}
```

A. 代码在“`if`”语句处无法编译。

B. 在“`if`”语句处运行时抛出异常。

C. 显示文本“`true`”。

D. 显示文本“`false`”。

E. 什么都不显示。

<details>
<summary>查看答案</summary>

### 正确答案：C

这道题在 `if` 语句的表达式中使用了赋值操作符 `=` 而不是相等性操作符 `==`。

执行到 `if` 语句时，程序首先执行 `valueOf` 方法，用于将基本数据类型 `boolean` 转换为包装类 `Boolean` 对象（自动装箱）：

```java
public static Boolean valueOf(boolean b) {
    return (b ? TRUE : FALSE);
}
```

此时 会将 `Boolean.TRUE` 赋值给`flag`。接着，程序会调用 `booleanValue` 方法，用于返回基本数据类型 `boolean`（自动拆箱）：

```java
public boolean booleanValue() {
    return value;
}
```

由于这里 `flag` 对象已经修改为 `Boolean.TRUE` ，因此该方法返回 `true`，执行`if`语句，而不会执行`else`语句，因此输出 `true`。

</details>

---

【多选题】以下说法错误的是（ ）？

A. final修饰的方法不能被重载

B. final可以修饰类、接口、抽象类、方法和属性

C. final修饰的方法也不能被重写

D. final修饰的属性是常量，不可以修改

<details>
<summary> 查看答案</summary>

### 正确答案：A B

A. final修饰的方法不能重写，但并不影响重载。

B. final不能修饰抽象类和接口

</details>

---


## 面向对象编程（OOP）

【单选题】已知`String a="a"`，`String b="b"`，`String c=a+b`，`String d=new String("ab")`，以下操作结果为`true`的是：

A. `(a+b).equals(c)`

B. `a+b==c`

C. `c==d`

D. `c.equals(d)`

<details>
<summary> 查看答案</summary>


### 正确答案：A和D

知识点总结：

### 1. == 和 equals() 比较：

- **== 操作符：**
  - 用于比较基本数据类型时，比较的是值。
  - 用于比较引用类型时，比较的是引用指向的地址。

- **equals() 方法：**
  - 在Object类中，其作用与 == 相同。
  - 在String类中，被重写，比较的是对象中的内容。

### 2. String对象的两种创建方式：

- **第一种方式：**
  - `String str1 = "aaa";`
  - 字符串字面量在常量池中创建，如果常量池中已存在，则直接引用。

- **第二种方式：**
  - `String str2 = new String("aaa");`
  - 会在堆中和常量池中（如果常量池中还没有相同的字符串对象）创建两个对象。

- **比较：**
  - `System.out.println(str1 == str2); // false`

### 3. String类型的常量池：

- **两种使用方法：**
  - 直接使用双引号声明的String对象会存储在常量池中。
  - 使用`String.intern()`方法，如果常量池中已包含相同内容的字符串，则返回常量池中的引用，否则在常量池中创建并返回引用。

- **示例：**
  ```java
  String s1 = new String("AAA");
  String s2 = s1.intern();
  String s3 = "AAA";
  System.out.println(s2);        // AAA
  System.out.println(s1 == s2);  // false
  System.out.println(s2 == s3);  // true
  ```

### 4. 字符串拼接：

- **不同方式的对象创建：**
  ```java
  String a = "a";             // 常量池中的对象
  String b = "b";             // 常量池中的对象
  String str1 = "a" + "b";   // 常量池中的对象
  String str2 = a + b;       // 在堆上创建的新对象
  String str3 = "ab";        // 常量池中的对象
  ```
- **比较：**
  ```java
  System.out.println(str1 == str2); // false
  System.out.println(str1 == str3); // true
  System.out.println(str2 == str3); // false
  ```

</details>

---

【单选题】**类 ABC 定义如下：**

```java
public  class  ABC{
    public  int  max( int  a, int  b) {  }
    /*expression*/
}
```


将以下哪个方法替换`expression`是不合法的（）。

- `A` :  `public float max(float a, float b, float c){ }`
- `B` :  `public int max (int c, int d){ }`
- `C` :  `public float max(float a, float b){ }`
- `D` :  `private int max(int a, int b, int c){ }`

<details>
<summary> 查看答案</summary>

### 正确答案：B

知识点：重载是在编译期通过方法中形参的静态类型确定调用方法版本的过程。重载是多态在编译期的表现形式。

重载的判定只有两个条件：（1）方法名一致；（2）形参列表不同

</details>

---

【单选题】**以下java程序代码，执行后的结果是（）**

```java
public class Test {
    public static void main(String[] args) {   
        Object o = new Object() {  
             public boolean equals(Object obj) {  
                 return true; 
         }
     };   
     System.out.println(o.equals("Fred"));
     }
}
```

- `A` :  `Fred`
- `B` :  `true`
- `C` :  `编译错误`
- `D` :  `运行时抛出异常`

<details>
<summary> 查看答案</summary>

### 正确答案：B

知识点：代码创建了一个匿名内部类的实例，并覆盖了equals方法，使其始终返回true。然后，通过o.equals("Fred")调用了这个覆盖后的equals方法。因此打印true。

相当于重写了一个永远返回true的equals()方法。

</details>


## 异常处理





## 集合框架

【多选题】**线程安全的map在JDK 1.5及其更高版本环境，有哪几种方法可以实现?**


- `A` :  `Map map = new HashMap()`
- `B` :  `Map map = new TreeMap()`
- `C` :  `Map map = new ConcurrentHashMap();`
- `D` :  `Map map = Collections.synchronizedMap(new HashMap());`

<details>
<summary> 查看答案</summary>

### 正确答案：C D

知识点：

1. `HashMap`，`TreeMap` 未进行同步考虑，是线程不安全的。 
2. `HashTable` 和 `ConcurrentHashMap` 都是线程安全的。区别在于他们对加锁的范围不同，`HashTable` 对整张`Hash`表进行加锁，而`ConcurrentHashMap`将`Hash`表分为`16`桶(`segment`)，每次只对需要的桶进行加锁。
3. `Collections` 类提供了`synchronizedXxx()`方法，可以将指定的集合包装成线程同步的集合，即使用同步机制保证多线程访问的安全性。比如：
   ```java
    List  list = Collections.synchronizedList(new ArrayList());
   
    Set  set = Collections.synchronizedSet(new HashSet());
   ```

</details>

---

【多选题】在Java中，关于HashMap类的描述，以下正确的是 ()

- `A` :  `HashMap使用键/值得形式保存数据`
- `B` :  `HashMap 能够保证其中元素的顺序`
- `C` :  `HashMap允许将null用作键`
- `D` :  `HashMap允许将null用作值`

<details>
<summary> 查看答案</summary>

### 正确答案：A C D

知识点：

`HashMap`不保证按照插入顺序排序，而是根据哈希值来确定元素在内部数组（`buckets`）中的位置，每个桶对应一个数组位置。当我们说"Map是无序的"时，我们指的是HashMap是无序的。实际上不同的Map实现在对元素的排序上有不同的策略：

1. `HashMap`: 无序。元素的顺序是根据哈希码和桶的顺序，不同于插入顺序。
2. `TreeMap`: 按照键的自然顺序或者通过构造方法提供的Comparator进行排序。
3. `LinkedHashMap`: 按照元素插入的顺序排序。保留了插入顺序。

|   Map集合类   |     key      |    value     |
| :-----------: | :----------: | :----------: |
|    HashMap    |  允许为null  |  允许为null  |
|    TreeMap    | 不允许为null |  允许为null  |
| ConcurrentMap | 不允许为null | 不允许为null |
|   HashTable   | 不允许为null | 不允许为null |

</details>

## 输入输出操作




## 数据结构与算法

【多选题】如果进栈序列为e1，e2，e3，e4，则可能的出栈序列是()

> 注：一个元素进栈后可以马上出栈，不用等全部进栈

- `A` :  `e3，e1，e4，e2`
- `B` :  `e2，e4，e3，e1`
- `C` :  `e2，e3，e4，e1`
- `D` :  `任意顺序都有可能`

<details>
<summary> 查看答案</summary>

### 正确答案：B C

使用代入法即可。

1. **对于 A 来说**：如果出栈顺序中 e3 要第一个出栈，那么必须先让e1和e2入栈，才能让e3入栈后再出栈。但是这样子就无法让e1作第二个出栈的，因为e1之前还有个e2，必须先把e2出栈了，e1才能出栈，所以不可能有e3、e1的出栈顺序。
2. **对于 B 来说**：画一个图：
   ```
   栈: [e1)             入栈 e1
   栈: [e1、e2)         入栈 e2
   栈: [e1)             出栈 e2: {e2}
   栈: [e1、e3)         入栈 e3
   栈: [e1、e3、e4)     入栈 e4
   栈: [e1、e3)         出栈 e4: {e2、e4}
   栈: [e1)             出栈 e3: {e2、e4、e3}
   栈: [)               出栈 e1: {e2、e4、e3、e1}
   ```
3. **对于 C 来说**：画一个图：
   ```
   栈: [e1)             入栈 e1
   栈: [e1、e2)         入栈 e2
   栈: [e1)             出栈 e2: {e2}
   栈: [e1、e3)         入栈 e3
   栈: [e1)             出栈 e3: {e2、e3}
   栈: [e1、e4)         入栈 e4
   栈: [e1)             出栈 e4: {e2、e3、e4}
   栈: [)               出栈 e1: {e2、e3、e4、e1}
   ```

</details>

## 多线程





## 网络编程





## 数据库连接





## Lambda表达式和流





## 设计模式





## Java 8新特性
