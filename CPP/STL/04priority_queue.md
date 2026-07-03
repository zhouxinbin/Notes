# priority_queue 优先队列

## 语法

```cpp
#include <queue>

//Type：数据类型
//Container：容器类型: 默认 vector<int>
//Functional：比较方式: greater（升序）、less（降序 默认 大根堆）
priority_queue(Type, Container, Functional)
```

## 大根堆

```cpp
priority_queue<int> a; // 大根堆
a.push(1); // 插入一个数
a.top(); // 取最大值
a.pop(); // 删除最大值
```

