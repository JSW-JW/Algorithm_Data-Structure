https://www.acmicpc.net/problem/2562 백준 2562번 문제

```
max_val = 0
max_val_order = -1
for i in range(9):
    input_num = int(input())
    if max_val < input_num:
        max_val = input_num
        max_val_order = i+1
        
print(max_val)
print(max_val_order)
```

shortened code


```
a = int(input())
b = int(input())
c = int(input())
multi_val = str(a*b*c)
for i in range(10):
    count = 0
    for j in range(len(multi_val)):
        if multi_val[j] == str(i):
            count += 1
    print(count)
```
```
a = int(input())
b = int(input())
c = int(input())
multi_val = str(a*b*c)
for i in range(10):
    res = multi_val.count(str(i))
    print(res)
```

shortend code
