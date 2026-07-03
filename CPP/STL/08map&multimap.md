# map 与 multimap

## 定义

- map 中所有的元素都是 pair
- pair 中第一个元素为 key（键值），第二个为 value（实值）。
- 所有元素都会根据元素的 key 进行排序

## 本质

关联式容器，二叉树实现

## 优点

可以根据 key 快速找到 value 的值

## 区别

- map 不允许有重复的 key
- multimap 可以有重复的 key

## 构造

```cpp
#include<map>
map<int, int> m;
map<int, int> m2(m); // 把 m 拷贝给 m2
```

## 函数

| 操作介绍                     | 调用示例                                              | 时间复杂度                |
| ---------------------------- | ----------------------------------------------------- | ------------------------- |
| 返回元素个数                 | `m.size();`                                           | O(1)                      |
| 判断容器是否为空             | `m.empty();`                                          | O(1)                      |
| 交换两个容器的内容           | `m.swap(other_map);`                                  | O(1)                      |
| 清空所有元素                 | `m.clear();`                                          | O(n)                      |
| 插入元素（单元素）           | `m.insert({1, 10});` 或 `m.insert(make_pair(1, 10));` | O(log n)                  |
| 删除迭代器所指元素           | `m.erase(pos);`（返回下一元素迭代器）                 | O(log n)                  |
| 删除区间 [begin, end) 内元素 | `m.erase(begin, end);`（返回下一元素迭代器）          | O(k + log n) k 为删除个数 |
| 删除键为 key 的元素          | `m.erase(key);`（返回删除个数，0 或 1）               | O(log n)                  |
| 查找键为 key 的元素          | `auto it = m.find(key);` 若不存在返回 `m.end()`       | O(log n)                  |
| 统计键为 key 的元素个数      | `int cnt = m.count(key);`（0 或 1，mutimap 可能 >1）  | O(log n)                  |