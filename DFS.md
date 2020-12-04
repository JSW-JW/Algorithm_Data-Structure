Source code from code signal (https://app.codesignal.com/interview-practice)


    def largestValuesInTreeRows(t):
        traverseAndLogTree(t, 0)
        return maxes


    def traverseAndLogTree(node, row):
        if not node:
            return

        if len(maxes) < row + 1:
            maxes.append(node.value)

        if maxes[row] < node.value:
            maxes[row] = node.value

        traverseAndLogTree(node.left, row + 1)
        traverseAndLogTree(node.right, row + 1)
    
*One of the way to search Node Tree and the way to solve it can be different depending on their perspectives.*

```
def digitTreeSum(t):
        stack = [(t, 0)]
        res = []
        sum = 0

    while stack:
        v, w = stack.pop()
        w = int(str(w) + str(v.value))
        if v.left or v.right:
            if v.left:
                stack.append((v.left, w))
            if v.right:
                stack.append((v.right, w))
        else:
            sum += w
    return sum
```
*My own code for the first time!*


