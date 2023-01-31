# 프로그래머스 마법의 엘리베이터
```python
def solution(storey):
    """
    현재 자릿수의 숫자 CUR 대해, 
    CUR = (1, 2, 3, 4) 인 경우 내리는 것이 유리
    CUR = (6, 7, 8, 9) 인 경우 올리는 것이 유리
    CUR = 5 인 경우 그 "위의 자리 수" 를 X 라고 할 때,
    X < 5 라면 내리는 것이 유리
    X >= 5 라면 올리는 것이 유리
    
    TEST CASE: 4445 -> 4 + 4 + 4 + 5 (17)
            5555 -> 1 + 4 + 4 + 4 + 5 (18)
    """
    ans = 0
    while storey != 0:
        up = False
        cur_digit = storey % 10
        storey //= 10 # 2554 -> 255
        if cur_digit < 5:
            ans += cur_digit
        elif cur_digit > 5:
            ans += (10 - cur_digit)
            up = True
        else:
            nxt_digit = storey % 10
            if nxt_digit < 5:
                ans += cur_digit
            else:
                ans += (10 - cur_digit)
                up = True

        if up: storey += 1
    
    return ans
```
