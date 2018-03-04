# lec2

## 思考题

* 一、中断；二、切换进程；三、清理内存；四、存取用于主存保护的寄存器等特权指令
* 实模式和保护模式的根本区别在于进程内存是否收到保护。实模式可以直接访问物理内存。物理地址是真实硬件上的地址；逻辑地址则是访问指令使用的地址；线性地址则是两者之间的变换的中间层。
* 表示对应域在结构体重占据的位数
* 0x20003

## 实践题

*   ```
    movl 4(%esp), %eax
    popl 0(%eax)
    movl %esp, 4(%eax)
    movl %ebx, 8(%eax)
    movl %ecx, 12(%eax)
    movl %edx, 16(%eax)
    movl %esi, 20(%eax)
    movl %edi, 24(%eax)
    movl %ebp, 28(%eax)
    ```
    保存寄存器中的数据
* 利用宏进行复杂数据结构中的数据访问；
  利用宏进行数据类型转换；
  ```
    #define to_struct(ptr, type, member) ((type *)((char *)(ptr) - offsetof(type, member)))
  ```
  常用功能的代码片段优化；
  ```
    #define ROUNDDOWN(a, n) ({size_t __a = (size_t)(a);(typeof(a))(__a -__a % (n));})
  ```