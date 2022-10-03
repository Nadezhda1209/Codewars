[Reversed Words](https://www.codewars.com/kata/51c8991dee245d7ddf00000e)

DESCRIPTION:
```
Complete the solution so that it reverses all of the words within the string passed in.

Example(Input --> Output):

"The greatest victory is that which requires no battle" --> "battle no requires which that is victory greatest The"
```
SOLUTION:
```
def reverse_words(s):
    s1 = s.split()
    s2 = s1[::-1]
    return (' '.join(s2))
```