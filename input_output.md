
  ```
  x = list(input() for _ in range(2))  # assign several lines(2 in this case) input into list.
  b = x[0]
  a = x[1]
  line_3 = 0
  line_4 = 0
  line_5 = 0
  tot = 0
  for i in range(len(a)):
      for j in range(len(b)):
          if i == 0:
              line_5 += int(a[i]) * int(b[j]) * 10**(2-j)
          if i == 1:
              line_4 += int(a[i]) * int(b[j]) * 10**(2-j)
          if i == 2:
              line_3 += int(a[i]) * int(b[j]) * 10**(2-j)
  tot = line_5 * 100 + line_4 * 10 + line_3
  print(line_3)
  print(line_4)
  print(line_5)
  print(tot)
  ```
