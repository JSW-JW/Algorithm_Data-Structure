# 프로그래머스 카카오 블라인드 파괴되지 않은 건물
[파괴되지 않은 건물](https://school.programmers.co.kr/learn/courses/30/lessons/92344)
```python
def solution(board, skill):
    n, m = len(board), len(board[0])
    a = [[0 for _ in range(m+1)] for _ in range(n+1)]
    def set_exit_point(r1, c1, r2, c2, degree):
        a[r1][c1] += degree
        a[r1][c2+1] -= degree
        a[r2+1][c1] -= degree
        a[r2+1][c2+1] += degree
    
    # 누적합 계산
    for sk in skill:
        tp, r1, c1, r2, c2, degree = sk
        if tp == 1:
            set_exit_point(r1, c1, r2, c2, -degree)
        elif tp == 2:
            set_exit_point(r1, c1, r2, c2, degree)
    for i in range(n+1):
        for j in range(1, m+1):
            a[i][j] += a[i][j-1]
    for j in range(m+1):
        for i in range(1, n+1):
            a[i][j] += a[i-1][j]
            
    # 건물에 누적합 최종 계산
    ans = 0
    for i in range(n):
        for j in range(m):
            board[i][j] += a[i][j]
            if board[i][j] > 0:
                ans += 1

    return ans
```
