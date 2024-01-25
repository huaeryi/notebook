# ROP
* 面向返回编程


### BufferOverflow
* 利用缓冲区溢出非法覆盖返回地址并返回到写入的shellcode

### ret2text
* 当NX栈不可执行时
* 返回到可执行代码段
### ret2shellcode
- 返回到一段恶意注入的shellcode
    * 可以在栈上
    * 也可以在bss段,如利用写函数恶意注入
### ret2syscall
- 返回到系统调用
    * 系统调用号存入`eax`
    * 函数参数存入其他寄存器
    * 用`int 80h`执行系统调用
* `ROPgadget`
### ret2libc
- 当程序中没有直接可以利用的函数时，返回到动态链接的libc库函数，通常是system
  * 返回到plt表，让plt帮你找
  * plt表没有，返回到真正的libc里
- linux动态链接 可执行文件->PLT表->GOT表->libc
  * PLT程序链接表
  * GOT全局偏移表
- 程序运行开始就建表是很麻烦的，延迟绑定机制plt->got->plt->公共plt->_dl_runtime_resolve
  * 第一次调用时写入，然后再次调用
  * 后续调用直接用
* libcsearcher
* libcdatabase
### ret2csu
* x64的传参前六个参数在寄存器RDI, RSI, RDX, RCX, R8, R9 


### ret2_dl_runtime_resolve
* 延迟绑定时所用函数

### BROP
* 在题目不给出二进制文件的情况下盲打
* 通过脚本遍历出二进制文件内容
* 进行其他ROP

### SROP