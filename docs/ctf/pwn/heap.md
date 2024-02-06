# Heap
* 堆漏洞利用

- chunk堆分配的数据结构
- 堆向上生长
- Glibc版本


### Use After Free(UAF)
* glibc-2.23
* 你可以使用释放后的堆
* 画内存图
### unlink
* 脱链
### ptmalloc2内存管理 ->Glibc使用的机制
- bin存放未分配或已释放chunk的机制
    * fast bin   单向链表
    * unsorted bin
    * large bin  循环双向链表
    * small bin  双向链表
    * tcache bin
### 函数
- `malloc`
    * 从小到达申请满足要求的堆块
- `free`
- 这些函数背后的系统调用主要是 (s)brk 函数以及 mmap, munmap 函数。

### off-by-one