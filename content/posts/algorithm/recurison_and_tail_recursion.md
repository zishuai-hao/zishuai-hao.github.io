# 递归与尾递归
递归函数在调用自身时会加深函数调用栈，保存前一个作用域的信息（java: 局部变量表，操作数栈，返回地址等），从而增加内存开销。并且一些编程语言中会对栈的深度进行限制，导致栈溢出。

尾递归是一种特殊的递归，在返回时执行递归函数调用，而不是在函数体中。由于当前函数作用域中的语句均执行完毕，无需保存相关的信息，因此可以在当前栈帧中直接调用下一个函数，从而避免了栈溢出的问题。仅有少数语言支持（C, ES6）。