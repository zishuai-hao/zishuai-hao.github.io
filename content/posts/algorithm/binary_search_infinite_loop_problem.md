# 二分法死循环问题
二分法有时候需要找到一个数字的插入位置，或者一个数字的删除位置，这个时候数组中不一定存在这个数字。这时候一般需要找到一个边界。

将找边界问题分为两类
1. 寻找第一个>=x的索引定义为寻找左边界
2. 寻找最后一个<=x的索引定义为寻找右边界

左右边界的界定主要是通过调整 mid 的位置，来确定边界。

如果找左边界，那么当 mid < x 时，边界应该设置为 (mid + 1, right) mid >= x (left, mid)
如果找右边界，那么当 mid > x 时，边界应该设置为 (left, mid -1 )  mid <= x (mid, right)


我们通常会这样计算 mid
```python
mid = left + (right - left) / 2
```
假设这种情况：
当 mid + 1 = right 时
=> mid = left + (right - left) / 2 = mid
=> mid 恒等于 left
这就是，寻找右边界时可能会存在的死循环问题，

解决方案是改为 left + right + 1, 另其向上取整


当寻找左边界时，mid 可以正常使用：
 mid = left + (right - left) / 2 = mid

因为 left < right（left >= right 说明已经获取结果）
=> (right - left) / 2 <= right - left
=> mid < left + right - left => mid < right 
不会陷入死循环
