# 프로그래머스 할인 행사

```python
from copy import deepcopy

def solution(want, number, discount):
    # 바3, 사2, 쌀2, 돼2, 냄비1
    # 치, 사, 사, 바, 쌀, 사, 돼, 바, 돼, 쌀, 냄, 바, 사, 바
    answer = 0
    d = dict(zip(want, number))
    for i in range(len(discount) - 9): # discount_idx = [0 ... 9]

        tmp = d[:]

        s = 0
        while s <10:
            p = discount[i+s]
            if tmp.get(p) == None:
                break
            else:
                tmp[p] -= 1
                if tmp[p] == 0:
                    del tmp[p]
            s += 1
                
        if len(tmp) == 0:
            answer += 1
    return answer

```
