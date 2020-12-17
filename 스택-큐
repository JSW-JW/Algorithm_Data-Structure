[프로그래머스 다리를 지나는 트럭](https://programmers.co.kr/learn/courses/30/lessons/42583)
```
from collections import deque
def solution(bridge_length, weight, truck_weights):
    answer = 0
    weight_sum = 0
    truck_weights = deque(truck_weights)
    
    accum = 0
    while truck_weights:
        w = truck_weights.popleft()
        weight_sum += w
        
        if truck_weights:
            if weight_sum + truck_weights[0] <= weight:
                accum += 1
                continue
            else:
                weight_sum = 0
                answer += (bridge_length + accum)
                accum = 0
        else:
            answer = answer + bridge_length + accum + 1
        
        
    return answer
```
