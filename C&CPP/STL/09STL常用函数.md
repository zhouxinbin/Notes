# STL 常用函数

## reverse

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

## unique

去重后返回重复元素的第一个迭代器。

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

**原理**

有序的容器：

| 1 | 1 | 2 | 3 | 3 | 4 | 4 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|---|---|---|

处理后的容器：

|      |      |      |      |      |      | 迭代器 |      |      |      |
| ---- | ---- | ---- | ---- | ---- | ---- | ------ | ---- | ---- | ---- |
| 1    | 2    | 3    | 4    | 5    | 6    | 1      | 2    | 4    | 4    |

`unique` 处理后，不重复的元素依次放在前面，多余重复元素放在后面，返回的迭代器指向重复元素的起始位置。

> 版权声明：本文为 CSDN 博主「Aggressive_snail」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
> 原文链接：https://blog.csdn.net/aggressive_snail/article/details/51332659

## random_shuffle

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

## sort

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

## lower_bound & upper_bound

- 均用于**已排序**范围（迭代器区间 `[first, last)`）的二分查找，返回**迭代器**（或指针）。
- 底层前提：区间必须按**升序**排列（或符合 `comp` 比较规则）。

**`lower_bound(first, last, value)`**

- 返回指向**第一个 >= value** 的元素的迭代器。
- 若所有元素都 `< value`，则返回 `last`。

**`upper_bound(first, last, value)`**

- 返回指向**第一个 > value** 的元素的迭代器。
- 若所有元素都 `≤ value`，则返回 `last`。

**常用场景**

- 查找 value 在已排序数组中的**可插入位置**（保持有序性）。
- 配合 `std::distance` 获取下标：`auto idx = lower_bound(v.begin(), v.end(), x) - v.begin();`
- 配合 `std::equal_range` 一次获取下界和上界（即 value 的所有出现范围）。

**注意事项**
- 区间需为随机访问迭代器（如 `vector`、数组），否则退化为线性查找。
- 自定义比较规则时，需保证严格弱序（如 `greater<int>()` 用于降序排序）。
- 若区间未排序，结果无意义（未定义行为）。

**示例**

```cpp
vector<int> v = {1, 2, 2, 3, 4};
auto low = lower_bound(v.begin(), v.end(), 2);  // 指向第一个 2
auto up  = upper_bound(v.begin(), v.end(), 2);  // 指向 3
// 区间 [low, up) 中元素均为 2（共 2 个）
```

## next_permutation

`next_permutation` 将序列变为字典序的下一个排列。存在下一排列返回 `true`，否则返回 `false`。

**获得全排列：**

```cpp
#include<algorithm>
#include<vector>
using namespace std;

class Solution {
public:
    vector<vector<int>> permutation(vector<int>& nums) {
        vector<vector<int>> s;
      	// 获得最小排列
        sort(nums.begin(), nums.end());
        do
        {
          	// 循环获得所有排列
            s.push_back(nums);
        } while (next_permutation(nums.begin(), nums.end()));
        return s;
    }
};
```

