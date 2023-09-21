

### 0-1背包
* 0-1背包指的是容量为W的背包，重量w[i]且价值v[i]的物品，每个物品只有两种状态，取或不取，怎样放入背包使背包中的物品价值最大。
* 二维数组解法，内存过大

=== "C++"

    ``` c++ linenums="1"
    #include<bits/stdc++.h>

    using namespace std;

    int w[1001];
    int v[1001];
    int dp[101][1001];

    int main()
    {
      int W, N;
      cin >> W >> N;
      for (int i = 1; i <= N; i++) {
        cin >> w[i] >> v[i];
      }
      for (int i = 0; i <= N; i++) {
        dp[i][0] = 0;
      }
      for (int i = 1; i <= N; i++) {
        for (int j = 1; j <= W; j++) {
          if (j < w[i]) {
            dp[i][j] = dp[i - 1][j];
          } else {
            dp[i][j] = max(dp[i - 1][j], dp[i - 1][j - w[i]] + v[i]);        
          }

        }
      }
      cout << dp[N][W];
      return 0;
    }
    ```


* 一维数组解法
=== "C++"

    ``` c++ linenums="1"
    #include<bits/stdc++.h>

    using namespace std;

    int w[1001];
    int v[1001];
    int dp[1001];

    int main()
    {
      dp[0] = 0;
      int W, N;
      cin >> W >> N;
      for (int i = 1; i <= N; i++) {
        cin >> w[i] >> v[i];
      }
      for (int i = 0; i <= N; i++) {
        for (int j = W; j >= w[i]; j--) {
          if (j - w[i] >= 0) {
            dp[j] = max(dp[j], dp[j - w[i]] + v[i]);
          }
        }
      }
      cout << dp[W];
      return 0;
    }
    ```

* [P1048 采药](https://www.luogu.com.cn/problem/P1048)
### 完全背包
* 在01背包的基础上，每个物品都可以取任意数量
=== "C++"

    ``` c++ linenums="1"
    #include<bits/stdc++.h>

    using namespace std;

    long long w[10001];
    long long v[10001];
    long long dp[10000001];

    int main()
    {
      long long W, n;
      cin >> W >> n;
      dp[0] = 0;
      for (int i = 1; i <= n; i++) {
        cin >> w[i] >> v[i];
      }
      for (int i = 1; i <= n; i++) {
        for (int j = w[i]; j <= W; j++) {
          dp[j] = max(dp[j], dp[j - w[i]] + v[i]);
        }
      }
      cout << dp[W];
      
      return 0;
    }
    ```
* [P1616 疯狂的采药](https://www.luogu.com.cn/problem/P1616)
