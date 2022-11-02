# 프로그래머스 택배상자 (lv.2)

```python
'''컨베이어 벨트로 상자 하나가 들어오는 것을 1라운드로 칠 때,
  적재되어 있는 것과 요청사항을 비교하는 과정은 라운드로 치지 않아야 한다 (i += 1 이 되지 않아야 한다) '''
def solution(order):
    sub = []
    box = 0
    # order = [4, 3, 1, 2, 5]
    temp = order.copy()
    idx = 0
    i = 0
    while i < len(order):
        ask = order[idx]
        if i+1 == ask:
            box += 1
            idx += 1
            i += 1
        elif sub and sub[-1] == ask:
            box += 1
            sub.pop()
            idx += 1
        else:
            sub.append(i+1)
            i += 1
            
    while sub:
        if order[idx] == sub[-1]:
            box += 1
            sub.pop()
            idx += 1
        else:
            break
    return box
```
