# nasm_study
汇编学习

1. 64位 nasm 学习网站
https://cs.lmu.edu/~ray/notes/nasmtutorial/

2. 32位 nasm 学习网站
https://asmtutor.com/#lesson1


坑
1. 在64位的情况下，不要用 INT80H 调用系统调动，需要用syscall   原因 ： ~ https://stackoverflow.com/questions/46087730/what-happens-if-you-use-the-32-bit-int-0x80-linux-abi-in-64-bit-code    ~  https://stackoverflow.com/questions/47023590/cant-print-a-linefeed-that-was-pushed-on-the-stack-in-nasm
2. 
根据System V AMD64 ABI规范我们，函数的前6个参数是通过寄存器来传递，其他的通过栈来传递。

rdi是第一个参数

rsi是第二个参数

rdx是第三个参数

rcx是第四个参数(如果系统调用函数的话是r10寄存器)

r8是第五个参数

r9是第六个参数

X86-64系统调用使用syscall指令.该指令将返回地址保存到rcx，会破坏rcx。所以使用r10寄存器了。

