# 壳

???+ abstract "加壳"

    加壳的全称应该是可执行程序资源压缩，是保护文件的常用手段。加壳过的程序可以直接运行，但是不能查看源代码。要经过脱壳才可以查看源代码。

  
### 压缩壳
* AsPack
* UPX
* PECompact
### 加密壳
* ASProtect
* Armadillo穿山甲
* EXECryptor
* Themida
* VMProtect

### 手脱
#### OEP
* OEP：(Original Entry Point)，程序的入口点。软件加壳一般隐藏了程序真实的OEP（或者用了假的OEP）， 我们需要寻找程序真正的OEP，才可以完成脱壳。

#### IAT
* IAT：(Import Address Table)，导入地址表。由于导入函数就是被程序调用但其执行代码又不在程序中的函数，这些函数的代码位于一个或者多个DLL中。


* esp定理
* 反调试绕过