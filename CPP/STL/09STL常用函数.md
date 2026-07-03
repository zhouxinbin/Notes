# STL 常用函数

## reverse 翻转

```cpp
#include<algorithm>
#include<iostream>
#include<vector>
using namespace std;

int main()
{
    vector<int> a = {1, 2, 3, 4, 5};
    reverse(a.begin(), a.end());
    int b[] = {1, 2, 3, 4, 5};
    reverse(b, b + 5);
    for (int i = 0; i < 5; i++) cout << a[i] << ' ';
    cout << endl;
    for (int c : b) cout << c << ' ';
    return 0;
}
```

## unique 去重

```cpp
#include<algorithm>
#include<iostream>
#include<vector>
using namespace std;

int main()
{
    vector<int> a = {1, 2, 2, 4, 5};
    int m = unique(a.begin(), a.end()) - a.begin();
    cout << m << endl;
    for (int i = 0; i < m; i++) cout << a[i] << ' ';
    cout << endl;
    a.erase(unique(a.begin(), a.end()), a.end());
    for (int c : a) cout << c << ' ';
    return 0;
}
```

`unique` 去重后返回重复元素的第一个迭代器。

### 原理

**有序的容器：**

| 1 | 1 | 2 | 3 | 3 | 4 | 4 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|---|---|---|

**处理后的容器：**

|      |      |      |      |      |      | 迭代器 |      |      |      |
| ---- | ---- | ---- | ---- | ---- | ---- | ------ | ---- | ---- | ---- |
| 1    | 2    | 3    | 4    | 5    | 6    | 1      | 2    | 4    | 4    |

`unique` 处理后，不重复的元素依次放在前面，多余重复元素放在后面，返回的迭代器指向重复元素的起始位置。

> 版权声明：本文为CSDN博主「Aggressive_snail」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
> 原文链接：https://blog.csdn.net/aggressive_snail/article/details/51332659

## random_shuffle 随机打乱

随机打乱容器内元素顺序，需先调用 `srand(time(0))` 设置随机种子。

```cpp
#include<algorithm>
#include<cstdlib>
#include<ctime>
#include<iostream>
#include<vector>
using namespace std;

int main()
{
    vector<int> a = {1, 2, 3, 4, 5};
    srand(time(0));
    random_shuffle(a.begin(), a.end());
    for (int b : a) cout << b << ' ';
    return 0;
}
```

## sort 排序

从小到大排序

```cpp
#include<algorithm>
#include<cstdlib>
#include<ctime>
#include<iostream>
#include<vector>
using namespace std;

bool cmp(int a, int b)
{
    return a < b;
}

int main()
{
    vector<int> a = {1, 2, 3, 4, 5};
    srand(time(0));
    random_shuffle(a.begin(), a.end());
    for (int b : a) cout << b << ' ';
    cout << endl;
    sort(a.begin(), a.end(), cmp);
    for (int b : a) cout << b << ' ';
    return 0;
}
```

## lower_bound 与 upper_bound

lower_bound 的第三个参数传入一个元素 x，
在两个迭代器（指针）指定的部分上执行二分查找，
返回指向第一个大于等于 x 的元素的位置的迭代器（指针）。

upper_bound 的用法和 lower_bound 大致相同，
唯一的区别是查找第一个大于 x 的元素。
当然，两个迭代器（指针）指定的部分应该是提前排好序的。

```cpp
#include<algorithm>
#include<iostream>
using namespace std;

int main()
{
    int a[] = {5, 8, 4};
    int t = upper_bound(a, a + 3, 8) - a;
    cout << a[t];
    return 0;
}
```

## next_permutation 全排列

`next_permutation` 将序列变为字典序的下一个排列。存在下一排列返回 `true`，否则返回 `false`。通常先 `sort` 以获得所有排列。

```cpp
#include<algorithm>
#include<vector>
using namespace std;

class Solution {
public:
    vector<vector<int>> permutation(vector<int>& nums) {
        vector<vector<int>> s;
        sort(nums.begin(), nums.end());
        do
        {
            s.push_back(nums);
        } while (next_permutation(nums.begin(), nums.end()));
        return s;
    }
};
```

