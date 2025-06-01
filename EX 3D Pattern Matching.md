# EX 3D Pattern Matching
## DATE:
## AIM:
To write a python program to implement pattern matching on the given string using Brute Force algorithm.

## Algorithm
1.Let m be the length of s1 (the big string).

2.Let n be the length of s2 (the pattern we want to find).

3.Loop through all possible starting positions in s1 where s2 could fit:From index 0 to m - n.

4.At each position i:Compare the substring of s1 starting at i with s2, character by character.

5.If all characters match (s1[i+j] == s2[j] for all j), then:

6.Return i as the starting index of the match.

7.If no match is found after checking all positions, return -1.
## Program:
```

# Developed by: SWETHA P
# Register Number: 212222100053

def BF(s1,s2):
    
    m=len(s1)
    n=len(s2)
    for i in range(m-n+1):
        j=0
        while j<n and s1[i+j]==s2[j]:
            j+=1
        if j==n:
            return i
    return -1
    
if __name__ == "__main__":
    a1=input() 
    a2=input() 
    b=BF(a1,a2)
    print(b)
```

## Output:
![image](https://github.com/user-attachments/assets/fb255d4c-7ac6-4c07-b38b-c90804ca86ac)

## Result:
The brute force substring search program executed successfully and returned the starting index of the match or 0 if no match was found.
