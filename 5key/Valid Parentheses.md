[Valid Parentheses](https://www.codewars.com/kata/52774a314c2333f0a7000688)


DESCRIPTION:
```

Write a function that takes a string of parentheses, and determines if the order of the parentheses is valid. The function should return true if the string is valid, and false if it's invalid.

Examples
"()"              =>  true
")(()))"          =>  false
"("               =>  false
"(())((()())())"  =>  true
Constraints
0 <= input.length <= 100

Along with opening (() and closing ()) parenthesis, input may contain any valid ASCII characters. Furthermore, the input string may be empty and/or not contain any parentheses at all. Do not treat other forms of brackets as parentheses (e.g. [], {}, <>).

```
SOLUTION:
```
def valid_parentheses(string):
    list1 = list(string)
    n=0
    for i in range(len(list1)):
        if list1[i]=="(":
            n+=1
        elif list1[i]==")":
            n-=1
            if n<0:
                return(False)
                break
        i+=1
    if n==0:
        return(True)
    else:
        return False
```