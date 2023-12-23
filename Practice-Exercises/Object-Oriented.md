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

【单选题】以下程序执行的结果是：

```java
class X{
    Y y=new Y();
    public X(){
        System.out.print("X");
    }
}
class Y{
    public Y(){
        System.out.print("Y");
    }
}
public class Z extends X{
    Y y=new Y();
    public Z(){
        System.out.print("Z");
    }
    public static void main(String[] args) {
        new Z();
    }
}
```

A. ZYXX

B. ZYXY

C. YXYZ

D. XYZX

<details>
<summary> 查看答案</summary>

**正确答案：C**

知识点：

我们来看一下类初始化过程中的顺序：

1. 父类的**静态成员变量**和**静态代码块**按照它们在类中的声明顺序依次执行。
2. 子类的**静态成员变量**和**静态代码块**按照它们在类中的声明顺序依次执行。
3. 父类的**实例成员变量**、**非静态代码块**按照它们在类中的声明顺序依次执行。
4. **父类的构造方法**执行。
5. 子类的**实例成员变量**、**非静态代码块**按照它们在类中的声明顺序依次执行。
6. **子类的构造方法**执行。

> 注意：对于静态成员变量和静态代码块，它们在类加载时就会执行，而不需要等到实例化对象。而实例成员变量、非静态代码块以及构造方法是在实例化对象时执行的。
>
> 另外，对于构造方法，子类的构造方法在执行时会先调用父类的构造方法，确保父类的初始化工作先完成。

按照这个流程，在这道题中：

1. 首先会初始化父类`X`的普通成员变量`y`。因此输出`Y`；
2. 接着执行父类`X`的构造方法，因此输出`X`；
3. 然后初始化子类的普通成员变量`y`，因此输出`Y`；
4. 最后执行子类的构造方法，输出`Z`。

</details>

---

【单选题】下列程序执行后结果为( )

```java
class A {
    public int func1(int a, int b) {
        return a - b;
    }
}
class B extends A {
    public int func1(int a, int b) {
        return a + b;
    }
}
public class ChildClass {
    public static void main(String[] args) {
        A a = new B();
        B b = new B();
        System.out.println("Result=" + a.func1(100, 50));
        System.out.println("Result=" + b.func1(100, 50));

    }
}
```

A. Result=150 Result=150

B. Result=100 Result=150

C. Result=150 Result=100

D. Result=50 Result=150

<details>
<summary> 查看答案</summary>

**正确答案：A**

知识点：

**“编译看左边，运行看右边”**，在编译时，Java会看左边引用类型是否能正确编译通过，而在运行时，实际执行的是对象的方法，即运行看右边。

对本题而言，编译时候会发现左边满足条件所以编译通过，运行时候又会调用右边也就是 `class B` 的方法，所以答案都是150。 

> **多态性**： 在Java中，多态性允许一个对象以多种形式存在。具体到这个例子中，对象a声明为A类，但实际上指向了B类的实例。这就是多态性的体现，一个对象可以被当作其父类类型来引用。
>
> **方法覆盖**： 在类B中，它继承了类A并覆盖了func1方法。方法覆盖是指在子类中重新定义（覆盖）父类中已有的方法。当子类对象调用这个方法时，会执行子类中的版本而不是父类中的版本。

</details>


---

【单选题】以下代码段执行后的输出结果为（）

```java
public class Test {
    public static void main(String[] args) {
        System.out.println(test());
 
    }
    private static int test() {
        int temp = 1;
        try {
            System.out.println(temp);
            return ++temp;
        } catch (Exception e) {
            System.out.println(temp);
            return ++temp;
        } finally {
            ++temp;
            System.out.println(temp);
        }
    }
}
```

A. 1 2 2

B. 1 2 3

C. 1 3 3

D. 1 3 2

<details>
<summary> 查看答案</summary>

**正确答案：D**

知识点：

这道题也有点意思。

就是`try`块中有`return`语句，也还是会执行`finally`块。

我们来看一下程序的执行顺序：

1. 程序进入`test()`方法，初始化`temp`为1。
2. 接着进入`try`块，打印并输出`temp`（1）；
3. 然后执行`return ++temp;`，此时`temp`变为2，返回值是2。
4. 注意！在`return`之前，程序会先将返回值保存着，然后执行`finally`块，最后再返回来执行`try`块的返回语句。
5. 因此进入`finally`块后，执行`++temp;`，此时`temp`变为3，然后打印并输出`temp`（3）。
6. 然后返回到`try`块中执行`return`语句，注意此时`return`语句返回的值是之前保存下来的temp值，即2。

因此，代码执行后的输出结果为：1 3 2。

我们可以再来看这个程序：

```java
public class Test {
    public static void main(String[] args) {
        System.out.println(test());
    }
    private static int test() {
        int temp = 1;
        try {
            System.out.println(temp);
            return temp++;  // 改为后置++
        } catch (Exception e) {
            System.out.println(temp);
            return ++temp;
        } finally {
            ++temp;
            System.out.println(temp);
        }
    }
}
```

将`try`块中的返回语句改为`后置++`，那么`return`语句中返回的值是`1`，该程序的输出结果为：

```bash
1
3
1
```

所以我们可以这么理解，运行时先执行`finally`块，`try`中`return`的值会先放入临时空间，当`finally`块执行完毕后再返回`try`中保存的值。

但需要注意的是，如果`finally`块中也有`return`语句，则会刷新临时空间的值。

比如下面这个程序：

```java
public class Test {
    public static void main(String[] args) {
        System.out.println(test());
    }
    private static int test() {
        int temp = 1;
        try {
            System.out.println(temp);
            return ++temp;
        } catch (Exception e) {
            System.out.println(temp);
            return ++temp;
        } finally {
            ++temp;
            System.out.println(temp);
            return temp;
        }
    }
}
```

运行结果为：

```bash
1
3
3
```

</details>

---

<!-- <details>
<summary> 查看答案</summary>

**正确答案：**

知识点：



</details> -->