<div align="center">

<h1>基础知识 (Basic Knowledge)</h1>

</div>

---

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

**正确答案：C**

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

A. `final`修饰的方法不能被重载

B. `final`可以修饰类、接口、抽象类、方法和属性

C. `final`修饰的方法也不能被重写

D. `final`修饰的属性是常量，不可以修改

<details>

<summary> 查看答案</summary>

**正确答案：A B**

A. `final`修饰的方法不能重写，但并不影响重载。

B. `final`不能修饰抽象类和接口

</details>

---

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

---

<!-- <details>
<summary> 查看答案</summary>

**正确答案：**

知识点：



</details> -->