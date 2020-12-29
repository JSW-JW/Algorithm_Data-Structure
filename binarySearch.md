```
n = int(input())
store_list = list(map(int, input().split()))
m = int(input())
order_list = list(map(int, input().split()))

store_list.sort()

def check_list(target_part, store_list, start, end):
  middle = (start + end ) // 2
  if store_list[middle] == target_part:
    return 'yes'
  
  elif start == end and store_list[start] != target_part:
    return 'no'
  
  elif store_list[middle] > target_part:
    if middle != 0:
        return check_list(target_part, store_list, start, middle - 1)
    else:
        return 'no'

  elif store_list[middle] < target_part:
    return check_list(target_part, store_list, middle+1, end)


for order in order_list:
  print(check_list(order, store_list, 0, len(store_list)-1), end=' ')
  
```

should state 'return' when calling function inside function and return the value, or it will return none.

**FOR EXAMPLE,** _this returns Null_
```
n = int(input())
store_list = list(map(int, input().split()))
m = int(input())
order_list = list(map(int, input().split()))

store_list.sort()

def check_list(target_part, store_list, start, end):
  middle = (start + end ) // 2
  if store_list[middle] == target_part:
    return 'yes'
  
  elif start == end and store_list[start] != target_part:
    return 'no'
  
  elif store_list[middle] > target_part:
    if middle != 0:
        check_list(target_part, store_list, start, middle - 1)
    else:
        return 'no'

  elif store_list[middle] < target_part:
    check_list(target_part, store_list, middle+1, end)


for order in order_list:
  print(check_list(order, store_list, 0, len(store_list)-1), end=' ')
```
