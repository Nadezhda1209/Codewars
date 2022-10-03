[Mexican Wave](https://www.codewars.com/kata/58f5c63f1e26ecda7e000029)

DESCRIPTION:
```
Task
In this simple Kata your task is to create a function that turns a string into a Mexican Wave. You will be passed a string and you must return that string in an array where an uppercase letter is a person standing up. 
Rules
 1.  The input string will always be lower case but maybe empty.

 2.  If the character in the string is whitespace then pass over it as if it was an empty seat
Example
wave("hello") => ["Hello", "hEllo", "heLlo", "helLo", "hellO"]
```
SOLUTION:
```
def wave(people):
    # Code here
    list1=list(people)
    new_word=[]
    for i in range(len(list1)):
        if list1[i]==" ":
            i+=1
        else:
            list1 = list(people)
            n1= list1[i]
            n1.upper()
            list1[i]= n1.upper()
            n11="".join(list1)
            new_word.append(n11)
    return(new_word)    
    pass
```