### 逆向工具
* 二进制编辑器
* IDA强大的逆向分析工具,keypatch补丁修改汇编指令
* PDB文件保存调试信息
* Ghidra
* studyPE
* `readelf`

### 壳
#### 压缩壳
#### 加密壳
### 代码混淆

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

