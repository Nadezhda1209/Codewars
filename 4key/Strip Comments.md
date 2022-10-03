[Strip Comments](https://www.codewars.com/kata/51c8e37cee245da6b40000bd)


DESCRIPTION:
```
Complete the solution so that it strips all text that follows any of a set of comment markers passed in. Any whitespace at the end of the line should also be stripped out.

Example:

Given an input string of:

apples, pears # and bananas
grapes
bananas !apples
The output expected would be:

apples, pears
grapes
bananas
The code would be called like so:

result = solution("apples, pears # and bananas\ngrapes\nbananas !apples", ["#", "!"])
# result should == "apples, pears\ngrapes\nbananas"
```
SOLUTION:
```
def strip_comments(strng, markers):
    len1= len(strng)
    def del_com(string1,com):
        index1 = string1.index(com)
        if string1[index1 - 1] == "\t":
            string1 = string1.replace("\t", "")
        index1 = string1.index(com)
        index2 = string1.find("\n", index1, len1 - 1)
        c = string1[index1:index2]
        if index2 < 0:
            if string1[index1 - 1] == "\n":
                string1 = string1[:index1 - 1] + "\n"
            else:
                string1 = string1[:index1 - 1]
        else:
            string1=list(string1)
            string1[index1:index2]=[]
            string1=''.join(string1)
            string1 = string1.replace(" \n", "\n")
            string1.strip()
        return(string1)
    for i in range(0,len(markers)):
        n1=markers[i]
        if n1 in strng:
            strng = del_com(strng, n1)
        i+=1
    for i in range(0,len(markers)):
        n1=markers[i]
        if n1 in strng:
            strng = del_com(strng, n1)
        i+=1
    for i in range(0,len(markers)):
        n1=markers[i]
        if n1 in strng:
            strng = del_com(strng, n1)
        i+=1
    for i in range(0,len(markers)):
        n1=markers[i]
        if n1 in strng:
            strng = del_com(strng, n1)
        i+=1
    #strng.rstrip()
    if len1>1:
        if strng[0]==" "and strng[1]=="\n":
            strng = list(strng)
            strng.pop(0)
            strng = ''.join(strng)
        if strng[-1] == " ":
            strng = list(strng)
            strng.pop(-1)
            strng = ''.join(strng)
    return(strng)
    pass
```