# nasm_study
汇编学习

1. 64位 nasm 学习网站
https://cs.lmu.edu/~ray/notes/nasmtutorial/

nasm汇编博客资料 （写的不错 ，通俗易懂）
https://blog.csdn.net/qq_31917799/category_9285609.html

2. 32位 nasm 学习网站
https://asmtutor.com/#lesson1

图文 汇编 学习资料
https://www.ruanyifeng.com/blog/2018/01/assembly-language-primer.html


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

3. 有压栈操作，一定要有对等的弹栈操作，不然会发生段错误 segment fault

4. 在gdb中，查看main函数反汇编代码

(在gdb中输入disassemble main)
反汇编一个函数
disass func_name


   参考资料 https://blog.csdn.net/m0_55708805/article/details/117388229?spm=1001.2101.3001.6650.8&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EOPENSEARCH%7ERate-8-117388229-blog-123806765.pc_relevant_multi_platform_featuressortv2dupreplace&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EOPENSEARCH%7ERate-8-117388229-blog-123806765.pc_relevant_multi_platform_featuressortv2dupreplace&utm_relevant_index=8
   
5. nasm汇编 GDB单步调试
参考地址 https://blog.csdn.net/qq_31917799/article/details/87915432
默认是gas汇编 
(gdb)set disassembly-flavor intel 可以修改为intel汇编

6. EIP 就是一个是记录运行到哪里了
   EBP 一个是函数的地址
   
7. 汇编写携程
资料1 ： https://note.isliberty.me/article/61
资料2 ： https://zhuanlan.zhihu.com/p/220025846



fmmpeg 视频处理命令行学习
①https://www.bilibili.com/read/cv17408017/
②https://www.bilibili.com/read/cv3159777/

视频按时间切割 
ffmpeg -ss 00:16:29 -to 00:23:03 -i "test.mp4" -vcodec copy -acodec copy cut.mp4 -y
无损提取音频
ffmpeg -i "cut.mp4" -vn -acodec copy A.aac
合并视频和声音
ffmpeg -i "cut.mp4" -i "cut.aac" -c copy -map 0:v:0 -map 1:a:0 "new.mp4"
