* 并查集的实现是一个森林，其中每个节点1-n刚开始都是独立的树的根节点，通过维护一个父节点数组来体现哪些节点在一棵树上，一个最基本的带有find和unite操作的并查集实现如下
???+ note "disjoint"

    === "C++"
    
        ``` c++ linenums="1"
        #include<bits/stdc++.h>

        using namespace std;

        struct dsu
        {
          vector<size_t> pa;

          explicit dsu(size_t size) : pa(size) {
            iota(pa.begin(), pa.end(), 0);
          }


          size_t dsu::find(size_t x)
          {
            return pa[x] == x ? x : pa[x] = find(pa[x]);
          }

          void dsu::unite(size_t x, size_t y)
          {
            pa[find(x)] = find(y);
          }

        };
        ```
