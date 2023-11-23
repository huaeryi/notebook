### 管辖范围

* `lowbit` 被定义为x二进制最低位1与后面0组成的数
???+ note "lowbit"
   
    === "C++"

        ``` c++ linenums="1"
        int lowbit(int x) {
          // x 的二进制中，最低位的 1 以及后面所有 0 组成的数。
          // lowbit(0b01011000) == 0b00001000
          //          ~~~~^~~~
          // lowbit(0b01110010) == 0b00000010
          //          ~~~~~~^~
          return x & -x;
        }
        ```
* c[x]管辖的数组范围是[x - lowbit + 1, x]的区间和
### 区间查询
* 那么我们可以利用前缀和与差分，快速查询区间信息
???+ note "getsum"
   
    === "C++"

        ``` c++ linenums="1"
        int getsum(int x) {  // a[1]..a[x]的和
          int ans = 0;
          while (x > 0) {
            ans = ans + c[x];
            x = x - lowbit(x);
          }
          return ans;
        }
        ```
### 单点加
* 我们需要修改所有含有a[x]的c[y],将其加上k
???+ note "add"
   
    === "C++"

        ``` c++ linenums="1"
        void add(int x, int k) {
          while (x <= n) {  // 不能越界
            c[x] = c[x] + k;
            x = x + lowbit(x);
          }
        }
        ```