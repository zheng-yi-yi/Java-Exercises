<div align="center">

<h1>面向对象 (Object-oriented Programming)</h1>

</div>

---


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

**正确答案：B**

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

**正确答案：B**

知识点：代码创建了一个匿名内部类的实例，并覆盖了`equals`方法，使其始终返回true。然后，通过`o.equals("Fred")`调用了这个覆盖后的`equals`方法。因此打印`true`。

相当于重写了一个永远返回`true`的`equals()`方法。

</details>

---