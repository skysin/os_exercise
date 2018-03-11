# lec3

## 3.1

* BIOS都是读取硬盘的0磁头、0柱面、1扇区的内容，然后把控制权交给这里面的MBR。因为一开始文件系统并没有建立，所以BIOS无法识别硬盘的存储内容，也就无法直接读入系统内核。
* 安全性更强：UEFI启动需要一个独立的分区，它将系统启动文件和操作系统本身隔离，可以更好的保护系统的启动。
启动配置更灵活：EFI启动和GRUB启动类似，在启动的时候可以调用EFIShell，在此可以加载指定硬件驱动，选择启动文件。
支持容量更大:传统的BIOS启动由于MBR的限制，默认是无法引导超过2TB以上的硬盘的。

## 3.2

* 0X55AA
* 通过启动前的数字签名检查来保证启动介质的安全性

## 3.3

* 中断：外部意外的响应；异常：指令执行意外的响应；系统调用：系统调用指令的响应；
* 源头、响应方式、处理机制
* ucore lab8的answer中共有22个系统调用，大致分为4类
  进程管理：包括 fork/exit/wait/exec/yield/kill/getpid/sleep
  文件操作：包括 open/close/read/write/seek/fstat/fsync/getcwd/getdirentry/dup
  内存管理：pgdir命令
  外设输出：putc命令 

## 3.6

* 指令不同，特权级不同，堆栈切换
* call:将当前的IP 或者 CS:IP 压入栈中，然后跳转到指定位置
  ret:用栈中所保存的数据赋值给IP的， 跳转回来。
  int：引发中断过程
  iret：用栈中的内容设置CS、IP和标志寄存器
  不同在于SS:SP压栈