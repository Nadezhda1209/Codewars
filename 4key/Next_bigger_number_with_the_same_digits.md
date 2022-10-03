[Next bigger number with the same digits](https://www.codewars.com/kata/55983863da40caa2c900004e)


DESCRIPTION:
```

Create a function that takes a positive integer and returns the next bigger number that can be formed by rearranging its digits. For example:

12 ==> 21
513 ==> 531
2017 ==> 2071
nextBigger(num: 12)   // returns 21
nextBigger(num: 513)  // returns 531
nextBigger(num: 2017) // returns 2071
If the digits can't be rearranged to form a bigger number, return -1 (or nil in Swift):

9 ==> -1
111 ==> -1
531 ==> -1
nextBigger(num: 9)   // returns nil
nextBigger(num: 111) // returns nil
nextBigger(num: 531) // returns nil
```
SOLUTION:
```
def next_bigger(n):
    mn = []
    n1 = [int(a) for a in str(n)]
    len1= len(n1)
    n1.reverse()
    if len1 == 1:
        return(-1)
    elif all(n1[i] <= n1[i + 1] for i in range(len(n1) - 1)):
        return(-1)
    i = 0
    while i<len(n1)-1:
        n1 = [int(a) for a in str(n)]
        n1.reverse()
        x_sr = n1[i]
        for j in range(i+1,len(n1)):
                n1 = [int(a) for a in str(n)]
                n1.reverse()
                if n1[j] < x_sr:
                        n1.insert(j+1, x_sr)
                        n1.remove(x_sr)
                        n1[0:j] = sorted(n1[0:j], reverse=True)
                        n1.reverse()
                        n2 = int(''.join(map(str, n1)))
                        mn.append(n2)
                else:
                        j+=1
        i +=1
    mn.append(n)
    mn.sort()
    index_n = mn.index(n)
    return(mn[index_n+1])
```