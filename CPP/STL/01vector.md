# vector

## 定义

vector 是变长数组，支持随机访问，不支持在任意位置 O(1) 插入。为了保证效率，元素的增删一般应该在末尾进行。

## 声明

```cpp
#include <vector>

vector<int> a; //相当于一个长度动态变化的 int 数组
vector<int> b[233]; //相当于第一维长 233，第二位长度动态变化的 int 数组

struct rec {…};
vector<rec> c; //自定义的结构体类型也可以保存在 vector 中
```

## 迭代器

迭代器就如同 STL 容器的指针，可以用 `*` 解引用。一个保存 int 类型的迭代器的声明：

```cpp
vector<int>::iterator it;
```

vector 的迭代器是**随机访问迭代器**

- vector 的迭代器与一个整数相加减，其行为和指针的移动类似。
- vector 的两个迭代器相减，其结果也和指针相减类似，得到两个迭代器对应下标之间的距离。

## 函数

| 操作介绍         | 构造方式（调用示例）                | 时间复杂度 |
| ---------------- | ----------------------------------- | ---------- |
| 默认构造         | `vector<T> v;`                      | O(1)       |
| 指定大小构造     | `vector<T> v(n);`                   | O(n)       |
| 指定大小+初始值  | `vector<T> v(n, val);`              | O(n)       |
| 初始化列表构造   | `vector<T> v = {a, b, c};`          | O(n)       |
| 拷贝赋值         | `v = other;`                        | O(n)       |
| 下标访问         | `v[i]`                              | O(1)       |
| 首元素           | `v.front()`                         | O(1)       |
| 尾元素           | `v.back()`                          | O(1)       |
| begin/end 迭代器 | `v.begin()`, `v.end()`              | O(1)       |
| 元素个数         | `v.size()`                          | O(1)       |
| 判空             | `v.empty()`                         | O(1)       |
| 当前容量         | `v.capacity()`                      | O(1)       |
| 预留容量         | `v.reserve(n)`                      | O(n)       |
| 调整大小         | `v.resize(n)` 或 `v.resize(n, val)` | O(n)       |
| 清空元素         | `v.clear()`                         | O(n)       |
| 尾部插入         | `v.push_back(val)`                  | O(1) 均摊  |
| 尾部删除         | `v.pop_back()`                      | O(1)       |
| 插入元素         | `v.insert(pos, val)`                | O(n)       |
| 删除元素         | `v.erase(pos)`                      | O(n)       |
| 交换两个 vector  | `v1.swap(v2)`                       | O(1)       |

## 遍历

```cpp
#include<iostream>
#include<vector>
using namespace std;
int main()
{
    vector<int> a = {1, 2, 3};
    vector<int>::iterator it;
    for (it = a.begin(); it != a.end(); it++) cout << *it << endl;
    for (int i = 0; i < a.size(); i++) cout << a[i] << endl;
    return 0;
}
```

## 示例代码

```cpp
#include<iostream>
#include<string>
#include<vector>
using namespace std;
struct Person
{
    string name;
    int age;
    Person(string mname, int mage)
    {
        name = mname;
        age = mage;
    }
};
int main()
{
    vector<Person*> p;
    Person p1("aaa", 111);
    Person p2("bbb", 222);
    Person p3("ccc", 333);
    p.push_back(&p1);
    p.push_back(&p2);
    p.push_back(&p3);
    for (vector<Person*>::iterator i = p.begin(); i != p.end(); i++)
        cout << (*i)->name << ' ' << (*i)->age << endl;
    return 0;
}
```