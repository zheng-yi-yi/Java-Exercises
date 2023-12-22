<div align="center">

<h1>集合 (Collections)</h1>

</div>

---

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

---


【多选题】在Java中，关于HashMap类的描述，以下正确的是 ()

- `A` :  `HashMap使用键/值得形式保存数据`
- `B` :  `HashMap 能够保证其中元素的顺序`
- `C` :  `HashMap允许将null用作键`
- `D` :  `HashMap允许将null用作值`

<details>
<summary> 查看答案</summary>

**正确答案：A C D**

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

---

