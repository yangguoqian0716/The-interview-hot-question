# 八股文高频问题

## C语言基础
### C语言中，内存泄露的原因
1. 动态分配的内存没有被释放：当你使用malloc，calloc或realloc函数动态分配内存后，如果你没有使用free函数来释放这些内存，那么这些内存就会一直存在，直到程序结束。这就是内存泄露。 
2. 指针赋值问题：如果指针指向动态分配的内存块，然后该指针被重新赋值而没有释放原来的内存，就会导致内存泄露。 
3. 重复释放内存：如果你试图释放已经被释放的内存，可能会导致程序崩溃。
4. 循环引用：如果存在循环引用的数据结构，例如双向链表，可能会导致内存泄露，因为即使没有指向数据结构的指针，它们仍然相互引用，导致内存无法释放。

### GCC编译步骤
1. 预处理 -E 展开宏、包头文件、替换条件编译、删除注释等
2. 编译   -S 检查语法错误
3. 汇编   -c 将汇编指令翻译成机器源码
4. 链接   该阶段最重要的是库函数（静态库和动态库）

### 静态链接和动态链接的区别
1. 静态链接在编译阶段完成，动态链接在程序运行时完成
2. 静态链接可执行文件包含了所有的目标代码和库函数代码，占用内存大，加载速度快
3. 动态链接生成的可执行文件更小，但更依赖于系统中已安装的共享库，加载速度慢

### 
