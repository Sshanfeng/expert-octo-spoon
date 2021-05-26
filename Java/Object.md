# Object
## 1. hashcode
- 我们把内存地址不同的对象成为不同的对象，内存地址相同的对象称为相同的对象。相等和相同不是同一个概念，相同一定相等，相等不一定相同。两个对象的相等是人为规定的，对象的相等是一个等价关系，必须满足等价性的条件，即自反性，对称性，传递性。另外还要再加上程序运行时的一致性，一致性是指只要equals中用于比较对象相等的信息没有发生变化，则equals的返回值相同
- 重写`equals`必须重写`hashcode`，因为要遵循`Object`的协议，即`c1.equals(c2)`蕴含着`c1.hashcode()==c2.hashcode()`
- `hashcode`用于`HashMap`中，对一个对象多次调用`hashcode`的值相同
- 如果两个对象通过`equals`的结果不同，它们的`hashcode`值不必不相同，然而这样会降低`hashMap`的性能
- `Object`中定义的`hashcode`对不同的对象返回不同的值

## 2. equals
- `equals`定义了非null对象上的的等价关系
- `equals`的多次调用返回值相同，只要`equals`使用的对象信息没有发生变化
- `x.equals(null)`返回`null`
- `Object`定义的`equals`能最大程度区分对象，只有两个变量指向相同的对象时，`equals`才会返回`true`
- 重写equals一般也需重写`hashcode`，这是为了保持`hashcode`和`equals`之间的协议，它要求相等的对象必须有相同的`hashcode`值
- equals相等，hashcode必相等，hashcode不相等，则equals必不相等

## clone
- `clone`会抛出`CloneNotSupportException`，如果对象的类没有实现`Cloneable`接口
- clone会创建一个对象的拷贝，由类来决定拷贝是什么样的，通常要满足
    `x.clone() != x`
    `x.clone().getClass() = x.getClass()`
    `x.clone().equals(x)`
    但这些都不是必须的
- 按照惯例，返回的对象独立于原对象，要做到这样，有时需要修改`super.clone`返回的对象，
- 浅拷贝和深拷贝
- 需要实现`Cloneable`接口才能拷贝，否则会抛出`CloneNotSupportedException`异常
- `Object`并没有实现`Cloneable`接口，所以调用`Object`的`clone`方法会抛出异常
- 数组的默认拷贝是浅拷贝，默认拷贝对基本数据类型的数组足够了，如果数组的元素是引用类型，并且要实现深拷贝，则需要改写`clone`方法
- 数组的拷贝有多种方法
    - `System.arraycopy`
    - `Arrays.copyOf和Arrays.copyOfRange`
    - `clone`
这几种方法都是浅拷贝，容器的默认拷贝也是浅拷贝。数组和容器的`clone`都是浅拷贝
- 可以利用序列化和反序列化实现深拷贝

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MzU4MzkwMDddfQ==
-->