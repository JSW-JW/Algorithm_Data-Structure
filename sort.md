
```
def solution(array, commands):
    answer = []
    for command in commands:
        f = command[0]-1
        b = command[1]
        sliced = array[f:b].sort()
        answer.append(sliced[command[2]-1])
    return answer
```
First try
```
 def solution(array, commands):
    answer = []
    for command in commands:
        i,j,k = command
        answer.append(list(sorted(array[i-1:j]))[k-1])
    return answer
```
More formatted code.

```
def solution(array, commands):
    return list(map(lambda x: sorted(array[x[0]-1:x[1]])[x[2]-1], commands))
```

single line code.. !!


[프로그래머스 가장 큰 수](https://programmers.co.kr/learn/courses/30/parts/12198)

```
def solution(numbers):
    answer = ''
    num_list = []
    for i in range(1, 10):
        for number in numbers:
            if str(number)[0] == str(10-i):
                num_list.append(str(number))
        if num_list:
            checkList(num_list, answer)
                
    return answer

def checkList(num_list, answer):
    ck_list = []
    int_num_list = list(map(int, num_list))
    max_len = len(str(max(int_num_list)))
    for i in range(max_len):
        for num in num_list:
            if len(num) == i+1:
                ck_list.append(int(num))
        while ck_list:
            max_val = max(ck_list)
            answer += str(max_val)
            ck_list.remove(max_val)
            
            
numbers = [6, 10, 2]
solution(numbers)
```
failed code.. Logic wrong at all.. :(
I should've known the way 'string' is sorted.

```
from itertools import permutations
def solution(num):
permute = list(permutations(num,len(num)))
list_permute = [''.join(map(str,i)) for i in permute]
answer = max(list_permute)
return answer
```
And if using permutations, it might be time over if 'N' is great enough.
```
def solution(numbers):
    numbers = list(map(str, numbers))
    numbers.sort(key = lambda x: x*3, reverse=True)
    return str(int(''.join(numbers)))
```

[프로그래머스 H-Index](https://programmers.co.kr/learn/courses/30/parts/12198)

```
def solution(citations):
    answer = 0
    cited = 0
    n = len(citations)
    for h in range(1, n+1):
        for citation in citations:
            if citation >= h:
                cited += 1
        if cited >= h:
            answer = h
            cited = 0
    return answer
```
