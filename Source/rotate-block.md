```python
arr = [
    [1,1,1],
    [1,0,0],
    [1,1,1]
    ]
    
def rotate(arr):
    copied = []
    for i in range(len(arr[0])):
        tmp = [arr[j][i] for j in range(len(arr)-1, -1, -1)]
        copied.append(tmp)
        
    return copied

print(*arr, sep='\n')
print()
for i in range(3):
    arr = rotate(arr)
    print(*arr, sep='\n')
    print()
```
