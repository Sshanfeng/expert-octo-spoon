# Java异常
## Error和Exception的联系
- `Error`和`Exception`都是继承于`Throwable`，`RuntimeException`继承自`Exception`。
- 异常分为受检查异常和不受检查异常。
    - 受检查的异常（checked exception, `IOException`等）：这类异常如果没有`try ... catch`也没有`throws`抛出，编译是通不过的。这类异常一般是外部错误，例如文件找不到、试图从文件尾后读取数据等，这并不是程序本身的错误，而是在应用环境中出现的外部错误。
    - 不受检查的异常（unchecked exception, `RuntimeException`等)：其特点是Java编译器不去检查它，也就是说，当程序中可能出现这类异常时，即使没有用`try ... catch`捕获，也没有用`throws`抛出，还是会编译通过，如除数为零的`ArithmeticException`、错误的类型转换、数组越界访问和试图访问空指针等。处理`RuntimeException`的原则是：如果出现`RuntimeException`，那么一定是程序员的错误。
- `Error`和`RuntimeException`及其子类称为未检查异常（Unchecked exception），其它异常成为受检查异常（Checked Exception）。
## try-catch-finally-return执行顺序
1. 不管是否有异常产生，finally块中代码都会执行；
2. 当try和catch中有return语句时，finally块仍然会执行；
3. finally是在return后面的表达式运算后执行的，所以函数返回值是在finally执行前确定的。无论finally中的代码怎么样，返回的值都不会改变，仍然是之前return语句中保存的值；
4. finally中最好不要包含return，否则程序会提前退出，返回值不是try或catch中保存的返回值。
### 举例
1. `try{} catch(){}finally{} return;`
按正常顺序执行。
2. `try{ return; }catch(){} finally{} return;`
程序执行`try`块中`return`之前（包括`return`语句中的表达式运算）代码；再执行`finally`块，最后执行`try`中`return`，`finally`块后面的return语句不再执行。
3. `try{ } catch(){return;} finally{} return;`
程序先执行`try`，如果遇到异常执行`catch`块，有异常：则执行`catch`中`return`之前（包括`return`语句中的表达式运算）代码，再执行`finally`语句中全部代码，最后执行`catch`块中`return`， `finally`块后面的`return`语句不再执行。无异常：执行完`try`再`finally`再执行最后的`return`语句
4. `try{ return; }catch(){} finally{return;}`
程序执行`try`块中`return`之前（包括`return`语句中的表达式运算）代码；再执行`finally`块，因为`finally`块中有`return`所以提前退出。
5. `try{} catch(){return;}finally{return;}`
程序执行`catch`块中`return`之前（包括`return`语句中的表达式运算）代码；再执行`finally`块，因为`finally`块中有`return`所以提前退出。
6. `try{ return;}catch(){return;} finally{return;}`
程序执行`try`块中`return`之前（包括`return`语句中的表达式运算）代码；有异常：执行`catch`块中`return`之前（包括`return`语句中的表达式运算）代码；则再执行`finally`块，因为`finally`块中有`return`所以提前退出。无异常：则再执行`finally`块，因为`finally`块中有`return`所以提前退出。

## 子类重写父类方法
1. 子类重写父类方法要抛出与父类一致的异常，或者不抛出异常
2. 子类重写父类方法所抛出的异常不能超过父类的范畴，也就是子类抛出的异常只能是父类异常的子类。
3. 重写方法一定不能抛出新的检查异常或者比被重写方法申明更加宽泛的检查型异常。例如：父类的一个方法申明了一个检查异常`IOException`，在重写这个方法是就不能抛出`Exception`,只能抛出`IOException`的子类异常，可以抛出非检查异常。
4. `RuntimeException`, `ArithmeticException`异常是运行期异常，子类重写的方法可以抛出任何运行期异常
8. 子类重写的方法可以抛出错误`Error`

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU2OTU4NDQzNV19
-->