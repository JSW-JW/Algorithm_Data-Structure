https://www.acmicpc.net/problem/2562 백준 2562번

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

shorten code

https://www.acmicpc.net/problem/2577 백준 2577번
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

shorten code


https://www.acmicpc.net/problem/3052 백준 3052번

```
input_list = []
count = 1
for _ in range(10):
    input_list.append(int(input())%42)
input_list.sort()
for i in range(len(input_list)-1):
    if input_list[i] != input_list[i+1]:
        count += 1
print(count)
        
```
Without 'set'

```
input_list = []
for _ in range(10):
    input_list.append(int(input())%42)
res = set(input_list)
    
print(len(res))
``` 
With 'set'
shorten code.
