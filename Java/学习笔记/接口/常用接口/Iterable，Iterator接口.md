# Iterable，Iterator接口

```java
//Iterable,Iterator接口源码

public interface Iterable<T>
{
	Iterator<T> iterator();
}

public interface Iterator<T>
{
	boolean hasNext();
	T next();
	void remove();
}
```

**Iterable接口：**它里面的只有一个返回Iterator实例的方法，这样设计的原因在于这样可以允许多种迭代方式并存。

**Iterator接口：**

* hasNext()：判断迭代是否到达终点，若有返回true，否则返回false
* next()：返回当前元素，“指针”指向当前元素后面的一个元素，要在hasNext()返回值为true的情况下调用
* remove()：删除最近由next()迭代出的元素

**注意事项：**

* Iterator接口中三个方法的调用顺序是有严格要求的，必须要先调用hasNext()，在确认可以进行迭代的情况下才能继续待用next()，最后才能调用remove()方法

  比如要删除第一个元素，必须先调用next()，再使用remove()，否则JVM会抛出异常

* 迭代出来的元素并不是元素本身，而是其拷贝。但是由于Java的引用机制，导致拷贝的结果还是引用。所以，若迭代对象是可变的，如：StringBuilder对象，则可以通过next()的返回的引用修改对象本身，但是若迭代对象不可变，如：String，通过next()返回的引用改变对象的值就无法作用到实际对象上了。

