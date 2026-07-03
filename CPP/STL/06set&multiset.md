# set & multiset

## 定义

所有元素插入时会自动排序

## 区别

set 不允许有重复元素
multiset 可以重复元素
set 插入数据会同时返回插入的结果，表示是否插入成功

## 声明

`#include<set>`
`set<int> st;`

## 函数

| 操作介绍                                                   | 调用示例              | 时间复杂度                   |
| ---------------------------------------------------------- | --------------------- | ---------------------------- |
| 插入数据                                                   | `s.insert(elem)`      | O(log n)                     |
| 清空所有元素                                               | `s.clear()`           | O(n)（析构元素）             |
| 返回元素个数                                               | `s.size()`            | O(1)                         |
| 判断容器是否为空                                           | `s.empty()`           | O(1)                         |
| 交换两个容器                                               | `s1.swap(s2)`         | O(1)                         |
| 删除迭代器 pos 处的元素，并返回下一元素的迭代器            | `s.erase(pos)`        | O(1) 均摊                    |
| 删除区间 [begin, end) 内的所有元素，并返回下一元素的迭代器 | `s.erase(begin, end)` | O(log n + 区间长度)          |
| 删除所有值为 elem 的元素，返回删除个数                     | `s.erase(elem)`       | O(log n + k)（k 为删除个数） |
| 查找 key 是否存在，返回迭代器（未找到则返回 `end()`）      | `s.find(key)`         | O(log n)                     |
| 统计 key 元素的个数（对 multiset 有用）                    | `s.count(key)`        | O(log n + k)（k 为个数）     |
| 查找大于等于 x 的最小元素，返回迭代器                      | `s.lower_bound(x)`    | O(log n)                     |
| 查找大于 x 的最小元素，返回迭代器                          | `s.upper_bound(x)`    | O(log n)                     |