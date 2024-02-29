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

【单选题】以下代码执行后输出结果为（ ）

```java
public class Test
{
    public static Test t1 = new Test();
    {
         System.out.println("blockA");
    }
    static
    {
        System.out.println("blockB");
    }
    public static void main(String[] args)
    {
        Test t2 = new Test();
    }
 }
```

A. blockAblockBblockA

B. blockAblockAblockB

C. blockBblockBblockA

D. blockBblockAblockB

<details>
<summary> 查看答案</summary>

**正确答案：A**

首先，需要明白类的加载顺序：

1. 父类静态对象和静态代码块
2. 子类静态对象和静态代码块 
3. 父类非静态对象和非静态代码块
4. 父类构造函数
5. 非静态对象和非静态代码块
6. 子类构造函数

其中：

- 类中静态块按照声明顺序执行
- 并且(1)和(2)不需要调用new类实例的时候就执行了(意思就是在类加载到方法区的时候执行的)

因而，整体的执行顺序为
  


```java
public class Test
{
    public static Test t1 = new Test();  //(1)
    {
         System.out.println("blockA");
    }
    static
    {
        System.out.println("blockB");  //(2)
    }
    public static void main(String[] args)
    {
        Test t2 = new Test(); //(3)
    }
 }
```

在执行(1)时创建了一个Test对象，在这个过程中会执行非静态代码块和缺省的无参构造函数，在执行非静态代码块时就输出了blockA；然后执行(2)输出blockB；执行(3)的过程同样会执行非静态代码块和缺省的无参构造函数，在执行非静态代码块时输出blockA。因此，最终的结果为：

```bash
blockA
blockB
blockA
```

至于对`t1`进行初始化时，为什么不先执行`static`代码块，而是先执行构造代码块。这是因为**静态成员变量和静态代码块的优先级是相同的**，先定义的先执行，如果把静态代码块放在静态成员前面，则输出 `BAA`，可以自己试一下。

</details>

---

【判断题】静态内部类不可以直接访问外围类的非静态数据，而非静态内部类可以直接访问外围类的数据，包括私有数据。（ ）

A. 正确

B. 错误

<details>
<summary> 查看答案</summary>

**正确答案：A**

总结：

对于**非静态内部类**来说：

1. 可以访问外围类的非静态数据，包括私有数据
2. 可以访问外围类的静态数据，包括静态私有数据

对于**静态内部类**来说：

1. 不能访问外围类的非静态数据
2. 可以访问外围类的静态数据，包括静态私有数据


</details>

---


【判断题】接口不能扩展（继承）多个接口。（ ）

A. 正确

B. 错误

<details>
<summary> 查看答案</summary>

**正确答案：B**

在Java中，一个接口可以扩展（继承）多个接口。这是Java支持的一种形式的多重继承。

> Java中类是单继承，但接口可以多继承，`Interfere1 extends Interface2,Interface3...`


</details>

---

【选择题】下面关于volatile的功能说法正确的是哪个（）

A. 原子性

B. 有序性

C. 可见性

D. 持久性

<details>
<summary> 查看答案</summary>

**正确答案：B C**

A选项，`volatile`关键字对任意单个`volatile`变量的的读写操作可以保证原子性，但类似于`volatile++`这种复合操作就无法保证原子性了。如果需要对这种复合操作保证原子性，最好用`synchronized`关键字。即`synchronized`保证三大性，原子性，有序性，可见性，`volatile`保证有序性，可见性，不能保证原子性。

B选项，为了实现`volatile`的内存语义，编译器在生成字节码时会在指令序列中插入内存屏障来禁止特定类型的处理器重排序，以此来保证有序性。

C选项，可见性是指当多个线程并发访问共享变量时，一个线程对共享变量的修改，其它线程能够立即看到。对于一个`volatile`变量的读，总是能看到对这个`volatile`变量最后的写入，保证了可见性。

D选项为干扰选项。

</details>

---


【选择题】下列哪个对访问修饰符作用范围由大到小排列是正确的？

A. `private>default>protected>public`

B. `public>default>protected>private`

C. `private>protected>default>public`

D. `public>protected>default>private`

<details>
<summary> 查看答案</summary>

**正确答案：D**

- `public` 可以被当前类，子类，包，其他包访问；
- `protected` 可以被当前类，子类，包访问；
- `default` 可以被可以被当前类，包内访问；
- `private` 只能被当前类访问。

</details>

---

3.有关线程的哪些叙述是对的（）

A. 一旦一个线程被创建，它就立即开始运行。

B. 使用start()方法可以使一个线程成为可运行的，但是它不一定立即开始运行。

C. 当一个线程因为抢先机制而停止运行，它可能被放在可运行队列的前面。

D. 一个线程可能因为不同的原因停止并进入就绪状态。

<details>

<summary> 查看答案</summary>

**正确答案：BCD**

选项A是错误的，因为线程在被创建后并不会立即开始运行。线程的生命周期包括新建、就绪、运行、阻塞和结束五个状态。当线程被创建后，它首先进入新建状态，然后通过调用`start()`方法进入就绪状态，等待系统的线程调度器调度。

选项B是正确的，调用`start()`方法会使线程进入就绪状态，但并不意味着线程会立即开始运行。线程何时开始运行取决于操作系统的线程调度策略。

选项C也是正确的，当一个线程因为抢先机制而暂停运行，它可能被放在可运行队列的前面。这是因为在抢先式调度策略中，优先级高的线程总是优先于优先级低的线程运行。

选项D是正确的，一个线程可能因为各种原因（如等待I/O操作完成、等待获取锁等）从运行状态变为阻塞状态，当这些条件满足后，线程又会重新进入就绪状态，等待线程调度器的调度。

</details>

---

<!-- <details>
<summary> 查看答案</summary>

**正确答案：**

知识点：



</details> -->