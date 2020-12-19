
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
