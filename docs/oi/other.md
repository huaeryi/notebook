### 高精度
* 高精度计算利用字符串和竖式加减法实现大整数的四则运算
???+ Abstract "高精度"

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
???+ Abstract "快速幂"

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
???+ Abstract "欧几里得算法"

    === "C++"

        ``` c++ linenums="1"
        int gcd(int a, int b) {
          if (b == 0) return a;
          return gcd(b, a % b);
        }

        //迭代
        int gcd(int a, int b) {
          while (b != 0) {
            int t = a;
            a = b;
            b = t % b;
          }
          return a;
        }

        int lcm(int a, int b) {
          return a * b / gcd(a, b);
        }
        ```
* 扩展欧几里得算法，用于求解形如$ax + by = gcd(a, b)$的一组解
???+ Abstract "扩展欧几里得算法"

    === "C++"

        ``` c++ linenums="1"
        int Exgcd(int a, int b, int &x, int &y) {
          if (!b) {
            x = 1;
            y = 0;
            return a;
          }
          int d = Exgcd(b, a % b, x, y);
          int t = x;
          x = y;
          y = t - (a / b) * y;
          return d;
        }
        ```

### 离散化
* 将不好用作下标的数组数据根据元素间的大小关系哈希，从而得到离散化数组，可以作为某些复杂问题的预处理
???+ Abstract "离散化"

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

### 筛法
* 埃氏筛法朴素的思想是，把一个素数的倍数都筛去，最后留下的就是素数，不加证明地给出时间复杂度$O(nloglogn)$
???+ Abstract "埃氏筛法"

    === "C++"

        ``` c++ linenums="1"
        bool is_prime[N];
        int Eratosthenes(int n) {
          int p = 0;
          for (int i = 0; i <= n; ++i) is_prime[i] = 1;
          is_prime[0] = is_prime[1] = 0;
          for (int i = 2; i <= n; ++i) {
            if (is_prime[i]) {
              prime[p++] = i;  // prime[p]是i,后置自增运算代表当前素数数量
              if ((long long)i * i <= n)
                for (int j = i * i; j <= n; j += i)
                  // 因为从 2 到 i - 1 的倍数我们之前筛过了，这里直接从 i
                  // 的倍数开始，提高了运行速度
                  is_prime[j] = 0;  // 是i的倍数的均不是素数
            }
          }
          return p;
        }
        ```
        
* 线性欧拉筛法的思想是，让每个合数都只被标记一次，时间复杂度来到$O(n)$

