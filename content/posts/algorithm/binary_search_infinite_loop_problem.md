# 二分法死循环问题

当寻找第一个>=x的索引时，
会设置边界为 
  if mid_val <= target_val: left = mid
当 left + 1 = right 时
那么 mid = left + (right - left) / 2 = mid
=> mid 恒等于 left, 陷入死循环

当寻找最后一个<=x的索引时，
会设置边界为
if mid_val >= target_val: right = mid
当 left < right 时
那么 mid = left + (right - left) / 2 = mid
因为 left < right, (right - left) / 2 <= right - left
=> mid < left + right - left => mid < right 
不会陷入死循环
