[Beginner - Reduce but Grow](https://www.codewars.com/kata/57f780909f7e8e3183000078)

DESCRIPTION:
```
Given a non-empty array of integers, return the result of multiplying the values together in order. Example:

[1, 2, 3, 4] => 1 * 2 * 3 * 4 = 24
```
SOLUTION:
```
def grow(arr):
    x=1
    for i in arr:
        x*=i
    return(x)
        
    #return(reduce(lambda x, y: x*y, l))
    pass
```