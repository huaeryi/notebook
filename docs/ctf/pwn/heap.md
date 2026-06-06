# Heap
???+ abstract
    - 堆漏洞利用
    - chunk堆分配的数据结构
    - 堆向上生长
    - Glibc版本不同造成漏洞的利用方式不同
    - ![](https://img.shields.io/badge/-Glibc2.29-informational?style=flat-square)
    ![](https://img.shields.io/badge/-Glibc2.29-red?style=flat-square)
    ![](https://img.shields.io/badge/-Glibc2.29-blueviolet?style=flat-square)


### ptmalloc2内存管理 ->Glibc使用的机制
- bin存放未分配或已释放chunk的机制
    * fast bin   单向链表
    * unsorted bin
    * large bin  循环双向链表
    * small bin  双向链表
    * tcache bin
### 函数
- `malloc`
    * 从小到大申请满足要求的堆块
- `free`
- 这些函数背后的系统调用主要是 (s)brk 函数以及 mmap, munmap 函数。

### Use After Free(UAF)
* glibc-2.23
* 你可以使用释放后的堆
* 画内存图
- 一般的利用方法是，先malloc一个堆块，然后free，如果程序没有对free后的指针做置空处理，就会形成悬垂指针（Dangling pointer），此时再malloc一个同样大小的堆块，就可以在释放后重新使用原来的堆
### unlink
- 关键函数绕过
???+ abstract "unlink"

    === "C"

        ``` c linenums="1"
        /** 伪造如下
        chunk = 0x602280
        P_fd = chunk - 0x18 = 0x602268
        P_bk = chunk - 0x10 = 0x602270
        */
        #define unlink(P, BK, FD)                                                  
        {                                                                          
            FD = P->fd;                                                            
            BK = P->bk;                                                            
            /** 关键判断
            FD->bk = *(chunk + 0x18) = 0x602268 + 0x18 = 0x602280 = P
            FD->fd = *(chunk + 0x10) = 0x602270 + 0x10 = 0x602280 = P
            这样就绕过了判断
            */
            if (__builtin_expect(FD->bk != P || BK->fd != P, 0))                   
                malloc_printerr(check_action, "corrupted double-linked list", P, AV);                                               
            //对chunk P执行解链操作
            else {                                                                 
                FD->bk = BK;                                                       
                BK->fd = FD; 
            ...
        ```
- 和off-by-one结合，溢出一个字节，修改堆块的P标志位为0，让堆块认为前一个堆块空闲，free后向前合并，形成大堆块。
- 效果就是往chunk里写入chunk-0x18的值，此时修改堆，就能修改到chunk-0x18地址上的内容，可以通过修改got表完成free函数的劫持，如劫持为puts泄露地址，劫持为system拿shell，最后再free掉一个含有"/bin/sh\x00"的堆块地址拿到shell


<!-- - __free_hook劫持 -->

  
### 堆溢出

### off-by-one
- 堆叠（Overlap）

#### off-by-null

### fastbin attack
#### fastbin double free
- fastbin是单向链表，fd指向下一个空闲块
- 该漏洞可以实现任意地址写
- `add(1) add(2) free(1) free(2) free(1)`
- main_arena->chunk1->chunk2->chunk1
- 此时chunk1的fd指针是指向chunk2的而不是null
- `add(3, addr) add(4) add(5) add(6, data)`实现任意地址写
    * 流程为chunk1脱离fastbin，fd指向addr
    * chunk2脱离fastbin
    * chunk1脱离fastbin，此时3 5指向的都是chunk1，其fd指向addr
    * addr作为一个chunk被分配出来，addr所指向的地址写入data

### tcache attack
#### tcache poisoning

### unsorted bin attack
- 循环双向链表
- free后show可以获得一个与main_arena有固定偏移的地址，这个偏移x可以通过调试得出
- main_arena在libc中的偏移计算
    * `__malloc_trim`函数分析偏移
    * `main_arena_offset = ELF("libc.so.6").symbols["__malloc_hook"] + 0x10`
- `libc_base = addr - x - main_arena_offset`
- 从而泄露libc基址

     



