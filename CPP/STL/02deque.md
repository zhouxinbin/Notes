# deque

## 定义

双端数组，可以对**头段**进行插入删除操作，与 vector 差不多

## 声明

```cpp
#include<deque>
deque<int> d;
```

## 函数

| 操作             | 函数                                     | 时间复杂度                            |
| ---------------- | ---------------------------------------- | ------------------------------------- |
| 尾部插入         | `push_back(val)`                         | 常数 O(1)                             |
| 头部插入         | `push_front(val)`                        | 常数 O(1)                             |
| 尾部删除         | `pop_back()`                             | 常数 O(1)                             |
| 头部删除         | `pop_front()`                            | 常数 O(1)                             |
| 访问首元素       | `front()`                                | 常数                                  |
| 访问尾元素       | `back()`                                 | 常数                                  |
| 随机访问（索引） | `operator[]` / `at(i)`                   | 常数 O(1)（比 vector 稍慢但仍是常数） |
| 插入中间         | `insert(pos, val)`                       | 线性 O(n)                             |
| 删除中间         | `erase(pos)` / `erase(first, last)`      | 线性 O(n)                             |
| 大小 / 判空      | `size()` / `empty()`                     | 常数                                  |
| 清空             | `clear()`                                | 线性 O(n)                             |
| 调整大小         | `resize(n)`                              | 线性 O(n)                             |
| 交换             | `swap(other)`                            | 常数                                  |
| 迭代器           | `begin()`, `end()`, `rbegin()`, `rend()` | 常数                                  |

## 代码

```cpp
#include<algorithm>
#include<deque>
#include<iostream>
using namespace std;
void printDeque(const deque<int>& d)
{
    for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)
        cout << *it << " ";
    cout << endl;
}
int main()
{
    deque<int> d;
    d.push_back(1);
    d.push_back(2);
    d.push_front(10);
    d.push_front(20);
    printDeque(d);
    sort(d.begin(), d.end());
    printDeque(d);
    return 0;
}
```

