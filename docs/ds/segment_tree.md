* 线段树是用于维护区间信息的一种数据结构，涵盖树状数组的功能
### 构建线段树
???+ note "build"
   
    === "C++"

        ``` c++ linenums="1"
        void build(int s, int t, int p) {
          // 对 [s,t] 区间建立线段树,当前根的编号为 p
          if (s == t) {
            d[p] = a[s];
            return;
          }
          int m = s + ((t - s) >> 1);
          // 移位运算符的优先级小于加减法，所以加上括号
          // 如果写成 (s + t) >> 1 可能会超出 int 范围
          build(s, m, p * 2), build(m + 1, t, p * 2 + 1);
          // 递归对左右区间建树
          d[p] = d[p * 2] + d[(p * 2) + 1];
        }
        ```

### 区间查询
???+ note "getsum"
   
    === "C++"

        ``` c++ linenums="1"
        int getsum(int l, int r, int s, int t, int p) {
          // [l, r] 为查询区间, [s, t] 为当前节点包含的区间, p 为当前节点的编号
          if (l <= s && t <= r)
            return d[p];  // 当前区间为询问区间的子集时直接返回当前区间的和
          int m = s + ((t - s) >> 1), sum = 0;
          if (l <= m) sum += getsum(l, r, s, m, p * 2);
          // 如果左儿子代表的区间 [s, m] 与询问区间有交集, 则递归查询左儿子
          if (r > m) sum += getsum(l, r, m + 1, t, p * 2 + 1);
          // 如果右儿子代表的区间 [m + 1, t] 与询问区间有交集, 则递归查询右儿子
          return sum;
        }
        ```

### 区间修改