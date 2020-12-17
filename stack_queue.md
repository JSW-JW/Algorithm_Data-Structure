[프로그래머스 프린터](https://programmers.co.kr/learn/courses/30/parts/12081)

```
from collections import deque
def solution(priorities, location):
    answer = 0
    my_file_pos = location
    priorities = deque(priorities)
    
    while priorities:
        cycle = False
        v = priorities.popleft()
        for priority in priorities:
            if v < priority:
                cycle = True
                priorities.append(v)
                if my_file_pos == 0:
                    my_file_pos = len(priorities)-1
                else:
                    my_file_pos -= 1
                break
        if not cycle:
            answer += 1
            if my_file_pos == 0:
                return answer
            else:
                my_file_pos -= 1
```


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
**My Wrong Code**

refactor

```
from collections import deque
def solution(bridge_length, weight, truck_weights):
    bridge_on = deque([0] * bridge_length)
    truck_weights = deque(truck_weights)
    time = 0
    while truck_weights:
        time += 1
        if sum(bridge_on) + truck_weights[0] <= weight: 
            w = truck_weights.popleft()
            bridge_on.popleft()
            bridge_on.append(w)
        else:
            bridge_on.popleft()
            if truck_weights and sum(bridge_on) + truck_weights[0] <= weight :
                bridge_on.append(truck_weights.popleft())
            else:
                bridge_on.append(0)
                
    while sum(bridge_on) > 0:
        time += 1
        bridge_on.popleft()
        bridge_on.append(0)

    return time
```
1 test case time over
