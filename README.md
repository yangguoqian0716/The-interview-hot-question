C语言中，内存泄露的原因？检查内存泄露的方法及调试工具？

1.动态分配的内存没有被释放：当你使用malloc，calloc或realloc函数动态分配内存后，如果你没有使用free函数来释放这些内存，那么这些内存就会一直存在，直到程序结束。这就是内存泄露。
2.指针赋值问题：如果指针指向动态分配的内存块，然后该指针被重新赋值而没有释放原来的内存，就会导致内存泄露。
3.重复释放内存：如果你试图释放已经被释放的内存，可能会导致程序崩溃。
4.循环引用：如果存在循环引用的数据结构，例如双向链表，可能会导致内存泄露，因为即使没有指向数据结构的指针，它们仍然相互引用，导致内存无法释放。



代码段，包括二进制可执行代码；
数据段，包括已初始化的静态常量和全局变量；
BSS 段，包括未初始化的静态变量和全局变量；
堆段，包括动态分配的内存，从低地址开始向上增长；
文件映射段，包括动态库、共享内存等，从低地址开始向上增长（跟硬件和内核版本有关 (opens new window)）；
栈段，包括局部变量和函数调用的上下文等。栈的大小是固定的，一般是 8 MB。当然系统也提供了参数，以便我们自定义大小；


上图中的内存布局可以看到，代码段下面还有一段内存空间的（灰色部分），这一块区域是「保留区」，之所以要有保留区这是因为在大多数的系统里，
我们认为比较小数值的地址不是一个合法地址，例如，我们通常在 C 的代码里会将无效的指针赋值为 NULL。因此，这里会出现一段不可访问的内存保留区，
防止程序因为出现 bug，导致读或写了一些小内存地址的数据，而使得程序跑飞。
