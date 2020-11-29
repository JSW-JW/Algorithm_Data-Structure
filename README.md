# Algorithm_Data-Structure
Repository for studying and storing algorithm, data structure information

93p.

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
