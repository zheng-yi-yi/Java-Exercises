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







## 面向对象编程（OOP）

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
   栈: [e1)             出栈e2: {e2}
   栈: [e1、e3)         入栈 e3
   栈: [e1、e3、e4)     入栈 e4
   栈: [e1、e3)         出栈e4: {e2、e4}
   栈: [e1)             出栈e3: {e2、e4、e3}
   栈: [)               出栈e1: {e2、e4、e3、e1}
   ```
3. **对于 C 来说**：画一个图：
   ```
   栈: [e1)             入栈 e1
   栈: [e1、e2)         入栈 e2
   栈: [e1)             出栈e2: {e2}
   栈: [e1、e3)         入栈 e3
   栈: [e1)             出栈e3: {e2、e3}
   栈: [e1、e4)         入栈e4
   栈: [e1)             出栈e4: {e2、e3、e4}
   栈: [)               出栈e1: {e2、e3、e4、e1}
   ```

</details>

## 多线程





## 网络编程





## 数据库连接





## Lambda表达式和流





## 设计模式





## Java 8新特性
