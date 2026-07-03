# break 与 continue

break跳出循环
continue
不管if后面的语句 重复完循环后才执行后面的语句

```cpp
#include<stdio.h>

int main()
{
    int x, i;
    scanf("%d", &x);
    int isprime = 1;
    for (i = 2; i < x; i++) {
        if (x % i == 0) {
            isprime = 0;
            break;
        }
    }
    if (isprime == 1) {
        printf("是素数\n");
    } else {
        printf("不是素数\n");
    }
    return 0;
}
```
