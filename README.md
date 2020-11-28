# Algorithm_Data-Structure
Repository for studying and storing algorithm, data structure information

93p.

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
            if m == 0:  # in case m == -1, loop do not break. should watch out!
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


    greatestNum()
