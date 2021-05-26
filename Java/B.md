Comparator和Comparable
都可用来比较对象的次序
- `Comparable` 实现类重写 `compareTo` 方法时一般要求 `e1.compareTo(e2) == 0` 的结果要和 `e1.equals(e2)` 一致，而`e.compareTo(null)`应抛出异常`NullPointerException`，尽管`e.equals(null)`返回false。这样将来使用 `SortedSet` 等**根据类的自然排序进行排序**的集合容器时可以保证保存的数据的顺序和想象中一致。如果你往一个 `SortedSet` 中先后添加两个对象 a 和 b，a b 满足`(!a.equals(b) && a.compareTo(b) == 0)`，同时也没有另外指定个 Comparator，那当你添加完 a 再添加 b 时会添加失败返回 false, SortedSet 的 size 也不会增加，因为在 SortedSet 看来它们是相同的，而 SortedSet 中是不允许重复的。实际上所有实现了 Comparable 接口的 Java 核心类的结果都和 equlas 方法保持一致。
实现了 Comparable 接口的 List 或则数组可以使用 `Collections.sort()` 或者 `Arrays.sort()` 方法进行排序。
从上面内容可知使用自然排序需要类实现 Comparable，并且在内部重写 comparaTo 方法。
- 而 Comparator 则是在外部制定排序规则，然后作为排序策略参数传递给某些类，比如 `Collections.sort(), Arrays.sort()` 或者一些内部有序的集合（比如 SortedSet，SortedMap 等）。
使用方式主要分三步：
若要对Bar类进行排序
    (1) 创建一个 Comparator 接口的实现类，在 compare 方法中针对Bar类写排序规则
    (2) 将 Comparator 对象作为参数传递给排序类的某个方法
    (3) 向排序类中添加Bar类对象


### 总结
Java 中的两种排序方式：
1. Comparable 自然排序。（实体类实现）
2. Comparator 是定制排序。（无法修改实体类时，直接在调用方创建）

### Collections.sort和Arrays.sort
Collections是处理集合的，Arrays是处理数组的
它们都有两个重载方法，一个接受一个参数List，一个接受两个参数List和Comparator。如果List的元素实现了Comparable接口，使用前一个，如果没有，使用后一个，这是需要提供一个Comparator

### 三个概念
相同：==
相等：equals
大小：实现Comparable的compareTo方法
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTA0NjY5NzI5XX0=
-->