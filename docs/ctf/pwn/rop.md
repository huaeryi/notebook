# ROP
* 面向返回编程
* `ROPgadget`
* `onegadget`
* `ropper`

### BufferOverflow
* 利用缓冲区溢出非法覆盖返回地址并返回到写入的shellcode、后门函数、库函数或者系统调用
* 如果带canary(rbp-8 or ebp-4)，则通过某些方式泄露canary后覆盖canary使其不变

### ret2text
* 当NX栈不可执行时
* 返回到可执行代码段
### ret2shellcode
- 返回到一段恶意注入的shellcode
    * 可以在栈上
    * 也可以在bss段,如利用写函数恶意注入
### ROPgadget代码复用
- 反复劫持控制流，组合汇编代码，达到想要的目的

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
* 特别好用的gadget函数
* x64的传参前六个参数在寄存器RDI, RSI, RDX, RCX, R8, R9 

### ret2syscall
- 返回到系统调用
    * 系统调用号存入`eax`
    * 函数参数存入其他寄存器
    * 用`int 80h`执行系统调用
- 在32位的情形下，`execve("/bin/sh",NULL,NULL)`
    * 系统调用号，即 eax 应该为 0xb
    * 第一个参数，即 ebx 应该指向 /bin/sh 的地址，有时候执行 sh 的地址也可以。
    * 第二个参数，即 ecx 应该为 0
    * 第三个参数，即 edx 应该为 0

### stack pivot
- 栈迁移
    * leave->mov rsp, rbp + pop rbp (回退上一个函数的rsp和rbp)
    * ret->pop rip(回到返回地址处)
    * 如果先劫持rbp为target-4, rbp+4为leave_ret地址，mov rsp,rbp使得rsp指向了参数s-4的位置,rop rbp弹出栈顶的值(s-4)给rbp并且rsp=rsp+4,之后pop rip,把tatget处地址传给rip,我们就劫持了控制流，并且把栈迁移到一个足够的空间中
- offbyone/offbynull
    * 栈迁移里的这两个应该指的是我们只能溢出到rbp的最低有效字节,这一个字节可以是0-255，由此我们可以控制栈迁移到原来rbp相邻处，null就更严苛了，相当于这个字节只能是0x00，但同样改变了rbp的最后一个字节，使得栈迁移了

### ret2_dl_runtime_resolve
* 延迟绑定时所用函数

### BROP
* 在题目不给出二进制文件的情况下盲打
* 通过脚本遍历出二进制文件内容
* 进行其他ROP

### SROP
