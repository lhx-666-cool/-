```cpp
#include <iostream>
#include <vector>
 
class dsu {
public:
    std::vector<long long> pa;
    std::vector<long long> size;
    // 其他要维护的量
    // 构造函数中需要初始化维护的量
    dsu(long long n) : pa(n, 0), size(n, 1) {
        for (long long i = 0; i < n; ++i) {
            pa[i] = i;
        }
    }

    long long find(long long x) {
        if (pa[x] == x) {
            return x;
        } else {
            pa[x] = find(pa[x]);
            return pa[x];
        }
    }

    void unite(long long x, long long y) {
        long long px = find(x), py = find(y);
        if (px == py) {
            return;
        }
        // 按节点个数合并, 如不需要可删去(也可改为按秩合并)
        if (size[px] < size[py]) {
            std::swap(px, py);
        }
        pa[py] = px;
        size[px] += size[py];
        // 处理其他要维护的量
    }
};

int main() {
    return 0;
}
```
