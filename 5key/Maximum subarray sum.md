[Maximum subarray sum](https://www.codewars.com/kata/54521e9ec8e60bc4de000d6c)


DESCRIPTION:
```

The maximum sum subarray problem consists in finding the maximum sum of a contiguous subsequence in an array or list of integers:

max_sequence([-2, 1, -3, 4, -1, 2, 1, -5, 4])
# should be 6: [4, -1, 2, 1]
Easy case is when the list is made up of only positive numbers and the maximum sum is the sum of the whole array. If the list is made up of only negative numbers, return 0 instead.

Empty list is considered to have zero greatest sum. Note that the empty list or array is also a valid sublist/subarray.
```
SOLUTION:
```
def max_sequence(arr):
    if len(arr)==0:
        return(0)
    else:
        summ=[]
        i=0
        while i<len(arr)-1:
            s1=arr[i]
            for j in range(i+1,len(arr)):
                s1+=arr[j]
                summ.append(s1)
                j+=1
            i +=1
    summ.sort()
    summ1 = summ[-1]
    if summ1<0:
        return(0)
    else:
        return(summ[-1])
```