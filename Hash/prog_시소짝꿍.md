# 프로그래머스 시소 짝꿍
```python
from collections import Counter
import math

def solution(weights):
    """
    (1) 같은 weight:
        해당 weight 의 수 n 에 대하여 nC2
        
    (2) 다른 weight
        ex) (100, 2) -> (200 // 3), (200 // 4)
            (100, 3) -> (300 // 2), (300 // 4)
            (100, 4) -> (400 // 2), (400 // 3)
            
            (200, 2)
            (200, 3)
            (200, 4)
    """
    ans = 0
    c = Counter(weights)
    # 같은 weight:
    for k, v in c.items():
        if v > 1: ans += v * (v-1) / 2
    
    for i in range(len(weights)):
        acc = 0
        for j in range(2, 5):
            weight = j * weights[i]
            for dist in [k for k in [2, 3, 4] if k != j]:
                if weight % dist == 0 and c[weight // dist] > 0 and c[weights[i]] > 0:
                    ans += (c[weights[i]] * c[weight // dist])
        c[weights[i]] = -1
    
    return ans
```


#### 내가 생각하는 다른 분의 모범 답안
```python
from collections import defaultdict

def solution(weights):
    possible = [2.0, 4/3, 3/2]
    answer = 0
    weight_dict = defaultdict(int)

    n = len(weights)

    for weight in weights:
        weight_dict[weight] += 1

    for key, item in weight_dict.items():
        num = weight_dict[key]
        answer += num * (num - 1) // 2
        for mult in possible:
            value = key * mult

            if value.is_integer() and value in weight_dict.keys():
                answer += weight_dict[key] * weight_dict[int(value)]           



    return answer
```
