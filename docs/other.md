### 高精度
* 高精度计算利用字符串和竖式加减法实现大整数的四则运算
=== "C++"
    ``` c++ linenums="1"
    #include<bits/stdc++.h>

    using namespace std;

    static const int LEN = 1004;

    int a[LEN], b[LEN], c[LEN];


    void clear(int a[])
    {
      for (int i = 0; i < LEN; i++) {
        a[i] = 0;
      }
    }

    void read(int a[])
    {
      static char s[LEN + 1];
      scanf("%s", s);

      clear(a);

      int len = strlen(s);
      for (int i = 0; i < len; i++) {
        a[len - i - 1] = s[i] - '0';
      }
    }

    void print(int a[])
    {
      int i;
      for (i = LEN - 1; i >= 1; i--) {
        if (a[i] != 0) {
          break;
        }
      }
      for (; i >= 0; i--) {
        putchar(a[i] + '0');
      }
      putchar('\n');
    }

    void add(int a[], int b[], int c[])
    {
      clear(c);

      for (int i = 0; i < LEN - 1; i++) {
        c[i] += a[i] + b[i];
        if (c[i] >= 10) {
          c[i + 1] += 1;
          c[i] -= 10;
        }
      }
    }

    void sub(int a[], int b[], int c[]) {
      clear(c);

      for (int i = 0; i < LEN - 1; ++i) {
        c[i] += a[i] - b[i];
        if (c[i] < 0) {
          c[i + 1] -= 1;
          c[i] += 10;
        }
      }
    }

    int main()
    {
      read(a);
      read(b);
      add(a, b, c);
      print(c);
      return 0;
    }
    ```

### 快速幂
* 快速幂是以$\Theta(log \space n)$时间复杂度计算高次幂的小技巧
=== "C++"
    ``` c++ linenums="1"
    #include<bits/stdc++.h>

    using namespace std;

    //递归
    long long binpow(long long a, long long b)
    {
      if (b == 0) {
        return 1;
      }
      long long res = binpow(a, b / 2);
      if (b % 2) {
        return res * res * a;
      } else {
        return res * res;
      }
    }

    //非递归
    long long binpow(long long a, long long b)
    {
      long long res = 1;
      while (b > 0) {
        if (b & 1) res = res * a;
        a = a * a;
        b >>= 1;
      }
      return res;
    }
    ```
### gcd和lcm
* 最大公约数欧几里得算法
=== "C++"
    ``` c++ linenums="1"
    int gcd(int a, int b) {
      if (b == 0) return a;
      return gcd(b, a % b);
    }

    int lcm(int a, int b) {
      return a * b / gcd(a, b);
    }
    ```
* 扩展欧几里得算法

### 离散化
* 将不好用作下标的数组数据根据元素间的大小关系哈希，从而得到离散化数组，可以作为某些复杂问题的预处理
=== "C++"

    ``` c++ linenums="1"
    // arr[i] 为初始数组,下标范围为 [1, n]
    for (int i = 1; i <= n; ++i)  
      tmp[i] = arr[i];
    std::sort(tmp + 1, tmp + n + 1);                        
    int len = std::unique(tmp + 1, tmp + n + 1) - (tmp + 1);
    for (int i = 1; i <= n; ++i)                              
      arr[i] = std::lower_bound(tmp + 1, tmp + len + 1, arr[i]) - tmp;
    ```