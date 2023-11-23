### 排序 `sort`
=== "C++"
    ``` c++ linenums="1"
    int nums[100];

    //定义不同的cmp函数可以得到不同的排序
    bool cmp(int &a, int &b) {
      return a < b;
    }

    sort(nums, nums + n, cmp);
    ```

### 二分查找 `lower_bound()` `upper_bound()`
=== "C++"
    ``` c++ linenums="1"
    #include <algorithm>

    //取得最小的下标i使 a[i] >= x
    lower_bound(a,a+n,x)-a      //下标从0开始
    lower_bound(a+1,a+n+1,x)-a  //下标从1开始

    //取得最小的下标i使 a[i] > x
    upper_bound(a,a+n,x)-a      //下标从0开始
    upper_bound(a+1,a+n+1,x)-a  //下标从1开始

    lower_bound(a,a+n,x, greater<int>())  //内置类型从大到小排序
    lower_bound(a,a+n,x, less<int>())  //内置类型从小到大排序
    ```

* 可以对比两函数返回值，若不同则找到了a[i] == x，差值即为x的个数
  
### set & map
=== "C++"
    ``` c++ linenums="1"
    set<int> st;
    for (auto i : st) {
      cout << *it << endl;
    }

    map<string, int> mp;
    for (auto it = mp.begin(); it != mp.end(); it++) {
      cout << it->first << endl;
      cout << it->second << endl;
    }
    ```

### deque
=== "C++"

    ``` c++ linenums="1"
    deque<pair<int, int> > dq;
    dq.push_back(pair<int, int>(i, j));
    ```

