# Java 中的 ArrayList 调用 set 函数导致异常

在 Java 中，使用构造函数 构造出ArrayList 时，直接使用 set 方法会提示 IndexBoundException 异常。 
由于 set 方法中会首先调用 rangeCheck  方法，检查边界，此时的 size 为0，因此会抛出异常。
```java
private void rangeCheck(int index) {
    if (index >= size)
        throw new IndexOutOfBoundsException(outOfBoundsMsg(index));
}
```
所以必须先用 for 循环 调用add 函数填充空值（null）后, 才能调用 set 函数设置。