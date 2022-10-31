# Programmers 햄버거 만들기
##### 한 세트 만들고 바로 연달아 만드는 경우가 있다고 착각해서, for loop 안에서 append 를 마지막에 해주도록 짰는데  
##### 다시 보니 그런 입력의 경우가 불가능하므로 append 를 먼저해도 아무 문제 없음.

```python
def solution(ingredient):
    answer = 0
    l = []
    for elem in ingredient:
        while len(l) >= 4 and l[-4::] == [1, 2, 3, 1]:
            answer += 1
            for _ in range(4):
                l.pop()
        l.append(elem)
    if len(l) >= 4 and l[-4::] == [1, 2, 3, 1]:
        answer += 1
            
    return answer
    #   1    2  3   4    5    6    7    8    9 
    # [야채, 빵, 빵, 야채, 고기, 빵, 야채, 고기, 빵]
    # 6번째 재료가 쌓였을 때 -> 3-6
    # 9번째 재료가 쌓였을 때 -> 2, 7-9
```
