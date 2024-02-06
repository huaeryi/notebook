# Reverse

### 逆向工具
* 二进制编辑器
* IDA强大的逆向分析工具,keypatch补丁修改汇编指令
* PDB文件保存调试信息
* Ghidra
* studyPE
* `readelf`
* ILSpy
* Ollydbg
* Exeinfo PE
* tip:为某些windows工具设置环境变量Path`C:\Users\91758\Desktop\tools\upx-4.2.1-win64\upx-4.2.1-win64`
### angr

### IDAPython

### crackme & keygenme
* 练习程序
* 注册码生成程序

### 代码混淆
#### 花指令
* od修改nop
* IDAPython脚本
```
import idc

for i in range(0x400BB7, 0x400BBC + 1):
    idc.patch_byte(i, 0x90)
```

#### SMC
- 自修改代码`Self Modifying Code，动态代码加密技术`
    * 利用IDAPython脚本还原被修改的代码，得到运行时函数
#### ollvm
#### 反调试

### 逆向常见算法
#### Base64
* 特征索引表`ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/`
* 变式：改变特征索引表
#### Tea/XTea/XXTea
* 特征magic number ：`0x9e3779b9`
#### MD5
* MD5`0x67452301，0xEFCDAB89，0x98BADCFE，0x10325476`
#### RC4/RC5/RC6
#### AES/DES/IDEA
#### SHA256/SHA1
* SHA1`0x67452301，0xEFCDAB89，0x98BADCFE，0x10325476，0xC3D2E1F0`

  
### 编译原理
#### 预处理(Preprocessing)
* `gcc -E hello.c -o hello.i`
* 头文件包含`#include`
* 宏替换`#define`
* 处理条件编译指令`#ifndef`
* 删除注释
* 保留`#pargma`编译器指令
#### 编译(Compilation)
* `gcc -S -masm=intel hello.i -o hello.s`

#### 汇编(Assembly)
* `gcc -c hello.s -o hello.o`
* `objdump -sd hello.o`查看二进制文件信息

#### 链接(Linking)
* `gcc hello.o -o hello.out`
* 地址和空间分配、符号决议、重定向

### x86汇编
* [参考资料](https://huaeryi.github.io/2023/04/24/x86/)
* 施工中...

### OS
* Windows->PE
* Linux->elf
* DOS->16bit

### VM虚拟机逆向