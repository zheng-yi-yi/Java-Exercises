<div align="center">

<h1>Java-Exercises</h1>

<p>🚀🚀🚀我的Java练习题仓库！</p>

</div>



<h2>目录</h2>

- [基础知识 (Basic Knowledge)](#基础知识-basic-knowledge)
- [面向对象 (Object-oriented Programming)](#面向对象-object-oriented-programming)
- [集合 (Collections)](#集合-collections)
- [Java虚拟机（Java Virtual Machine）](#java虚拟机java-virtual-machine)

---

# 基础知识 (Basic Knowledge)

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


**正确答案：B**

由于没有`break`语句，从`case 4`开始会一直执行到最后，`j`自加`3`次变成了`4`，最后结果返回`8`。

</details>

更多内容查看：[基础知识 (Basic Knowledge)](/Practice-Exercises/Basic-Knowledge.md)

---

# 面向对象 (Object-oriented Programming)

【单选题】已知`String a="a"`，`String b="b"`，`String c=a+b`，`String d=new String("ab")`，以下操作结果为`true`的是：

A. `(a+b).equals(c)`

B. `a+b==c`

C. `c==d`

D. `c.equals(d)`

<details>
<summary> 查看答案</summary>


> **正确答案：A和D**

知识点总结：

> **1. == 和 equals() 比较：**

- **== 操作符：**
  - 用于比较基本数据类型时，比较的是值。
  - 用于比较引用类型时，比较的是引用指向的地址。

- **equals() 方法：**
  - 在Object类中，其作用与 == 相同。
  - 在String类中，被重写，比较的是对象中的内容。

> **2. String对象的两种创建方式：**

- **第一种方式：**
  - `String str1 = "aaa";`
  - 字符串字面量在常量池中创建，如果常量池中已存在，则直接引用。

- **第二种方式：**
  - `String str2 = new String("aaa");`
  - 会在堆中和常量池中（如果常量池中还没有相同的字符串对象）创建两个对象。

- **比较：**
  - `System.out.println(str1 == str2); // false`

> **3. String类型的常量池：**

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

> **4. 字符串拼接：**

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

更多内容查看：[面向对象 (Object-oriented Programming)](/Practice-Exercises/Object-Oriented.md)


# 集合 (Collections)

【多选题】**线程安全的map在JDK 1.5及其更高版本环境，有哪几种方法可以实现?**


- `A` :  `Map map = new HashMap()`
- `B` :  `Map map = new TreeMap()`
- `C` :  `Map map = new ConcurrentHashMap();`
- `D` :  `Map map = Collections.synchronizedMap(new HashMap());`

<details>
<summary> 查看答案</summary>

**正确答案：C D**

知识点：

1. `HashMap`，`TreeMap` 未进行同步考虑，是线程不安全的。 
2. `HashTable` 和 `ConcurrentHashMap` 都是线程安全的。区别在于他们对加锁的范围不同，`HashTable` 对整张`Hash`表进行加锁，而`ConcurrentHashMap`将`Hash`表分为`16`桶(`segment`)，每次只对需要的桶进行加锁。
3. `Collections` 类提供了`synchronizedXxx()`方法，可以将指定的集合包装成线程同步的集合，即使用同步机制保证多线程访问的安全性。比如：
   ```java
    List  list = Collections.synchronizedList(new ArrayList());
   
    Set  set = Collections.synchronizedSet(new HashSet());
   ```

</details>

更多内容查看：[集合 (Collections)](/Practice-Exercises/Collections.md)

---

# Java虚拟机（Java Virtual Machine）

【多选题】以下哪些内存区域属于JVM规范？（　　）

A. 方法区

B. 实例变量

C. 静态变量

D. 程序计数器

E. 虚拟机栈

<details>
<summary> 查看答案</summary>

**正确答案：A D E**

知识点：

`Java` 虚拟机内存区域主要分为五个部分：程序计数器（ `PC` 寄存器）、虚拟机栈、本地方法栈、堆、方法区/元空间。

| 内存区域          | 描述                                                                                         |
| ----------------- | -------------------------------------------------------------------------------------------- |
| **程序计数器**    | 记录当前线程执行的字节码行号指示器。每个线程都有独立的程序计数器。                           |
| **虚拟机栈**      | 用于存储局部变量和方法调用的信息。每个线程在执行Java方法时拥有对应的虚拟机栈。               |
| **本地方法栈**    | 与虚拟机栈类似，为本地（Native）方法服务，执行本地方法时使用。                               |
| **堆**            | 存储对象实例，被所有线程共享。垃圾回收主要针对堆进行。                                       |
| **方法区/元空间** | 存储类的结构信息、常量、静态变量等。在Java 8及之前称为"永久代"，在Java 8及之后称为"元空间"。 |

具体细节：

1. **程序计数器：**
   - 每个线程都有一个独立的程序计数器（ `PC` 寄存器）。
   - 记录当前线程执行的字节码行号指示器，也就是记录线程当前执行到哪条指令了。
   - 在多线程环境下，会切换执行不同线程的任务。

2. **虚拟机栈：**
   - 为每个线程分配一个虚拟机栈。
   - 存储局部变量、操作数栈、动态链接、方法出口等信息。
   - 栈帧（Stack Frame）：每个方法在执行时都会创建一个栈帧，栈帧包含方法的局部变量表和操作数栈等信息。

3. **本地方法栈：**
   - 与虚拟机栈类似，为执行本地方法服务。
   - 本地方法是用其他语言（如C语言）编写的方法，通过Java Native Interface（JNI）调用。

4. **堆：**
   - 存储对象实例，被所有线程共享。
   - 主要进行垃圾回收的区域，通过垃圾回收器管理内存。

5. **方法区/元空间：**
   - 存储类的结构信息、常量、静态变量等。
   - 在Java 8及之前称为"永久代"，在Java 8及之后称为"元空间"。
   - 在元空间中，类的元数据被存储在本地内存中，而不是堆中。

</details>

更多内容查看：[Java虚拟机（Java Virtual Machine）](/Practice-Exercises/Java-Virtual-Machine.md)

---

<!-- # 异常处理 (Exception Handling) -->

<!-- # 反射机制 (Reflection Mechanism) -->

<!-- # 注解 (Annotations) -->

<!-- # 泛型 (Generics) -->

<!-- # IO (Input/Output) -->

<!-- # JDBC编程 (JDBC Programming) -->

<!-- # Web开发 (Web Development) -->