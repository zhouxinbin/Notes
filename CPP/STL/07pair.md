# pair 对组

成对出现的数据，利用对组可以返回两个数据

## 创建方式
```cpp
pair<int, int> p = make_pair(1, 2);
cout << p.first << ' ' << p.second;
```

```cpp
int main()
{
    pair<string, int> p = make_pair("zhouxinbin", 18);
    cout << p.first << ' ' << p.second;
    return 0;
}
```

`pair` 在 `sort` 排序中，优先以 `first` 从小到大排序