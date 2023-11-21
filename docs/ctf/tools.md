???+ abstract

    * 介绍ctf中一些常用的工具
### Python常用库
#### `struct`(Python内置)用于打包二进制数据
=== "Python"

    ``` python linenums="1"
    import struct
    struct.pack('>I',16)
    '\x00\x00\x00\x10'
    ```
* pack的第一个参数是处理指令，`'>I'` 的意思是：`>` 表示字节顺序是 Big-Endian，也就是网络序，`I` 表示 4 字节无符号整数。


#### `python-memcached`高性能的分布式内存对象缓存系统
=== "Python"

    ``` python linenums="1"
    import memcache
    mc = memcache.Client([ip_port], debug=0)
    print(mc.get("key"))
    ```


#### `pwntools` pwn常用库
* shellcode注入示例
    ``` python linenums="1"
    from pwn import *
    context(arch = 'i386', os = 'linux')

    r = remote('exploitme.example.com', 31337)
    # EXPLOIT CODE GOES HERE
    r.send(asm(shellcraft.sh()))
    r.interactive()
    ```

#### `gmpy2` 密码学常用库

#### `libnum` 数学计算常用库

### gdb
* gef
* peda
* gdbinit
* 当在64位linux中要执行32位程序时`sudo apt-get install libc6:i386`安装32位支持

### webshell
* 上传木马后，用webshell连接工具便捷操作
* 中国蚁剑


### 010editer
* 搜索
* 词频统计
