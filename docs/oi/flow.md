### 网络流相关
- [网络流24题](https://www.luogu.com.cn/problem/list?tag=332)


???+ Abstract "网络流" 

    ```cpp linenums="1"  hl_lines="2 3" 
    int main() {
      scanf("%d%d%d%d", &n, &m, &s, &t);
      while (m--) {
        int u, v, w;
        scanf("%d%d%d", &u, &v, &w);
        addedge(u, v, w);
      }
      printf("%d\n", dinic(s, t));
      return 0;
    }
    ```


### 最大流



### 最小割
