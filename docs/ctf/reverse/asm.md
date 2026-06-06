# x86汇编

???+ abstract

    - 记录x86汇编的相关内容以及和在IDA中的显示情况
    - [简明 x86 汇编指南](https://arthurchiao.art/blog/x86-asm-guide-zh/)

### AT&T 和 Intel 汇编语法
- AT&T `movl %esp, %ebp` `movl  0x0100, %eax`
- Intel `MOV EBP, ESP` `mov ebp, esp` `MOV EAX, [0100]`
- 以Intel语法为主，和IDA显示格式相同，大小写均可

### IDA汇编窗口
- Shift+F12 查看字符串窗口
- Alt+T 搜索内容
- Ctrl+T 继续查找下一个

### 寄存器

### 指令集