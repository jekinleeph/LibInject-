基于shellcode加载

[1]编写shellcode，shellcode是使用汇编语言写一段汇编程序，该程序实现so库的加载、so库函数查找以及执行库中的函数。

[2]通过远程进程pid，ATTACH到远程进程。

[3]获取远程进程寄存器值，并保存，以便注入完成后恢复进程原有状态。

[4]获取远程进程系统调用mmap、dlopen、dlsym调用地址。

[5]调用远程进程mmap分配一段存储空间，并在空间中写入shellcode、so库路径以及函数调用参数。

[6]执行远程进程shellcode代码。

[7]恢复远程进程寄存器。

[8]detach远程进程。