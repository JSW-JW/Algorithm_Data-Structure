**my mistake notes**


프로그래머스 베스트앨범
```
def solution(genres, plays):
    res = []
    prev = set(res)
    genre_set = set(genres)
    
    while prev != genre_set:  
        max_genre = get_max_genre(genres, plays, prev)
        prev.add(max_genre)

        greater_plays = -1
        max_count = 0
        
        while max_count < 2:
            for i, genre in enumerate(genres):
                if genre == max_genre and plays[i] != -1 and max_count < 2:
                    if greater_plays == plays[i]:
                        pass
                    else:
                        greater_plays=max(greater_plays, plays[i])
            max_count += 1
            
            for i in range(len(plays)):
                if plays[i] == greater_plays:
                    res.append(i)
                    plays[i] == -1
                    greater_plays = -1
    
        


def get_max_genre(genres, plays, prev = None):
    genre_plays = {}
    for i, genre in enumerate(genres):
        if genre not in genre_plays:
            genre_plays[genre] = plays[i]
        else:
            genre_plays[genre] += plays[i]
    max_val = -1
    for key in genre_plays:
        max_val = max(max_val, genre_plays[key])
    for key in genre_plays:
        if genre_plays[key] == max_val:
            return key
```





93p.

```
from time import time

def myMistake():
    n, m, k = map(int, input().split())
    data = list(map(int, input().split()))

    data.sort(reverse=True)
    first = data[0]
    second = data[1]
    print(data[0])
    print(data[1])

    result = 0

    while True:
        for i in range(k):
            result += first
            m -= 1
            if m == 0:
                break
        result += second
        m -= 1
        if m == 0:  # in case m == -1, loop do not break
            break

    print(result)


def getGreatestSum():
    n, m, k = map(int, input().split())
    data = list(map(int, input().split()))

    data.sort(reverse=True)
    first = data[0]
    second = data[1]
    print(data[0])
    print(data[1])

    result = 0

    while True:
        for i in range(k):
            if m == 0:
                break
            result += first
            m -= 1
        if m == 0:
            break
        result += second
        m -= 1

    print(result)


def greatestNum():

    n, m, k = map(int, input().split())
    data = list(map(int, input().split()))

    data.sort(reverse=True)

    first = data[0]
    second = data[1]
    result = 0

    if first == second:
        result = first * m
    else:
        if m > k:
            result = ((first * k) + second) * (m // (k+1)) + (first * (m % (k+1)))
        elif m == k:
            result = first * m

    print(result)


# def cardGame():

    # n, m = map(int, input().split())
    # # 입력값 받기
    #
    # data = list(map(int, input().split()))
    #
    # for i in range(len(n)):
    #     firstIndexList.append(data[i][0]) # 2차원 리스트에서 각 행을 sort() 한 후 첫번째 인덱스들을 비교하려고 했으나,
    # result = 0                            # 2차원 리스트를 입력값으로 받는 방법과, 2차원 리스트의 각 행을 조회하는 방법을 알지못함.
    # result = max(firstIndexList)
    # print(result)

# 96p.
def CardGame():
    n, m = map(int, input().split())
    minList = []

    for i in range(n):
        minNumber = 10001
        data = list(map(int, input().split()))  # 2차원 형태의 데이터를 for 문에서 각 행으로 받는다는 생각을 어떻게, 왜 하는가?
        for j in range(m):
            if data[j] < minNumber:
                minNumber = data[j]
            minList.append(minNumber)

    result = max(minList)
    print(result)


# 99p.
def getMinExecuteNum():
    n, k = map(int, input().split())
    execNum = 0

    start_time = time()
    while True:
        if n % k == 0:
            n = (n / k)
            execNum += 1
            if n == 1:
                break
        else:
            if n > k:
                execNum += (n % k)
                n -= (n % k)
            elif n < k:
                execNum += ((n % k) - 1)
                n -= ((n % k) - 1)
                break

    end_time = time()
    print(int(execNum))
    print(start_time - end_time)


getMinExecuteNum()

    def calMoveCase():
    current = input()
    column_list = ["a", "b", "c", "d", "e", "f", "g", "h"]

    column = current[0]
    # e.g: a
    row_position = int(current[1])
    # e.g: 3
    column_position = 0
    result = 0
    for i in range(len(column_list)):  # my awkward logic when I didn't know the concept: list of move case
        if column_list[i] == column:  # (dx, dy or tuple data)
            column_position = i + 1
    if 3 <= column_position <= 6:
        case = 2
    else:
        case = 1
    if 2 <= row_position <= 7:
        vertical = 2
    else:
        vertical = 1
    result += case * vertical
    if 3 <= row_position <= 6:
        case2 = 2
    else:
        case2 = 1
    if 2 <= column_position <= 7:
        horizon = 2
    else:
        horizon = 1
    result += case2 * horizon

    print(result)

# Implementation
def calculateMoveCase():
    cur_pos = input()
    row_pos = int(cur_pos[1])

    col_pos = int(ord(cur_pos[0])) - int(ord('a')) + 1

    step_x = [2, 2, -2, -2, 1, -1, 1, -1]
    step_y = [1, -1, 1, -1, 2, 2, -2, -2]

    count = 0
    for i in range(len(step_x)):
        mov_pos_x = col_pos + step_x[i]
        mov_pos_y = row_pos + step_y[i]
        if 1 <= mov_pos_x <= 8 and 1 <= mov_pos_y <= 8:
            count += 1
    print(count)


# 118p.
def calMapCase():
    n, m = map(int, input().split())
    a, b, d = map(int, input().split())

    trackwalk = []
    mapdata = []
    count = 0
    confrontsea = False
    for i in range(n):
        data = list(map(int, input().split()))
        mapdata.append(data)
    directions = [(3, -1), (2, -1), (1, 1), (0, 1)]
    while not confrontsea:
        d -= 1
        if d == -1:
            d = 3
        for direction in directions:
            if d == direction[0]:
                if direction[0] % 2 == 0:
                    predictPath = a + direction[1]
                    if (predictPath, b) not in trackwalk and mapdata[b][a] != 1:
                        count += 1
                        a = predictPath
                else:
                    predictPath = b + direction[1]
                    if (a, predictPath) not in trackwalk and mapdata[b][a] != 1:
                        count += 1
                        b = predictPath
    print(count)


def correctionMapCase():
    n, m = map(int, input().split())
    a, b, d = map(int, input().split())

    # 북, 동, 남, 서 (0, 1, 2, 3)
    track_walk = [[0] * m for _ in range(n)]
    mapInFo = []
    for i in range(n):
        mapInFo.append(list(map(int, input().split())))

    dirInfo = [(-1, 0), (0, 1), (1, 0), (0, -1)]
    turn_count = 0

    result = 1
    track_walk[a][b] = 1

    while True:
        d -= 1
        if d == -1:
            d = 3

        na = a + dirInfo[d][0]
        nb = b + dirInfo[d][1]
        if track_walk[na][nb] == 0 and mapInFo[na][nb] == 0:
            turn_count = 0
            result += 1
            a = na
            b = nb
            track_walk[na][nb] = 1
            continue
        else:
            turn_count += 1
        if turn_count == 4:
            a_back = a - dirInfo[d][0]
            b_back = b - dirInfo[d][1]
            if mapInFo[na][nb] == 0:
                a = a_back
                b = b_back
                track_walk[a][b] = 1
            else:
                break
            turn_count = 0
    print(result)


correctionMapCase()
```
