```
n = int(input())
count = 0
cycled_val = n
while True:
    prev = cycled_val % 10
    plus_val = (cycled_val // 10) + (cycled_val % 10)
    cycled_val = int(str(prev % 10) + str(plus_val % 10))
    count += 1
    if cycled_val == n:
        break
print(count)
```
