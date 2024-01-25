???+ abstract

    * 介绍ctf中一些常用的工具
    * [ctf tools](https://ctf-wiki.github.io/ctf-tools/)


### Python常用库
#### `struct`(Python内置)用于打包二进制数据
???+ abstract "struct"

    === "Python"

        ``` python linenums="1"
        import struct
        struct.pack('>I',16)
        '\x00\x00\x00\x10'
        ```
* pack的第一个参数是处理指令，`'>I'` 的意思是：`>` 表示字节顺序是 Big-Endian，也就是网络序，`I` 表示 4 字节无符号整数。


#### `python-memcached`高性能的分布式内存对象缓存系统
???+ abstract "python-memcached"

    === "Python"

        ``` python linenums="1"
        import memcache
        mc = memcache.Client([ip_port], debug=0)
        print(mc.get("key"))
        ```


#### `pwntools` pwn常用库
???+ abstract "shellcode注入示例"

    === "Python"

        ``` python linenums="1"
        from pwn import *
        context(arch = 'i386', os = 'linux')

        r = remote('exploitme.example.com', 31337)
        # EXPLOIT CODE GOES HERE
        r.send(asm(shellcraft.sh()))
        r.interactive()
        ```

#### `gmpy2` 密码学常用库

#### `libnum` 数学计算库

#### `socket` 网络接口库
* 自动化实现`nc`的python脚本
???+ abstract "socket"

    === "Python"

        ``` python linenums="1"
        import socket

        HOST = "10.214.160.100"  # IP address
        PORT = 12700           # Port number

        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)   # create socket

        s.connect((HOST, PORT))    # connect to this challenge

        def recv_one_line(socket):
            buf = b""
            while True:
                data = socket.recv(1)
                if data == b'\n':
                    return buf
                buf += data

        def recv_one_question(socket):
            buf = b""
            while True:
                data = socket.recv(1)
                if data == b'=':
                    return buf
                buf += data
        ```
#### `requests` HTTP请求和爬虫常用库
???+ abstract "requests"

    === "Python"

        ``` python linenums="1"
        import requests

        x = requests.request('get', 'https://note.huaeryi.top/')

        print(x.status_code)
        ```

#### `z3-solver` 约束求解库
???+ abstract "requests"

    === "Python"

        ``` python linenums="1"
        import z3

        ```

### jupyter
* ipynb形式
* [在线python运行](https://jupyter.org/)
* 或者使用vscode的jupyter插件


### gdb
* gef
* peda
* gdbinit
* 当在64位linux中要执行32位程序时`sudo apt-get install libc6:i386`安装32位支持

### webshell
- 上传木马后，用webshell连接工具便捷操作
    * 中国蚁剑
    * 中国菜刀


### 010editer
* 搜索
* 词频统计
