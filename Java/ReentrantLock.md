
### ReentrantLock
- 等待可中断 通过`lock.lockInterruptibly()`放弃等待，改为处理其他
- 公平锁 `ReentrantLock(boolean fair)`
- 选择性通知
  `synchronized`关键字与`wait()`和`notify()`/`notifyAll()`方法相结合可以实现等待/通知机制。`ReentrantLock`类当然也可以实现，但是需要借助于`Condition`接口与`newCondition()`方法。


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTczMDU3NjA0NF19
-->