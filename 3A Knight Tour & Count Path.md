# EX 3A Knight Tour & Count Path
## DATE:
## AIM:
To write a python program to find minimum steps to reach to specific cell in minimum moves by knight


## Algorithm
1.Create a list of 8 possible moves a knight can make (because a knight moves in "L" shapes).

2.Create a queue to keep track of where the knight can move next.

3.Start by putting the knight’s starting position into the queue, with 0 steps taken so far.

4.Make a visited matrix to mark which positions the knight has already visited, so it doesn’t repeat positions.

5.Start looping:Take the front position from the queue.

6.If it is the target position, return the number of steps taken so far — you’re done!

7.If it’s not the target:Try all 8 possible knight moves from the current position.

8.For each move:Check if the new position is inside the board boundaries.

9.If it's valid and not visited:Mark it as visited.

10.Add it to the queue with the step count increased by 1.

11.Keep repeating this process until the target is reached.
## Program:
```
# Developed by: SWETHA P
# Register Number: 212222100053

class cell:
     
    def __init__(self, x = 0, y = 0, dist = 0):
        self.x = x
        self.y = y
        self.dist = dist

def isInside(x, y, N):
    if (x >= 1 and x <= N and
        y >= 1 and y <= N):
        return True
    return False
def minStepToReachTarget(knightpos,targetpos, N):
     # add your code here
    dx = [2, 2, -2, -2, 1, 1, -1, -1]
    dy = [1, -1, 1, -1, 2, -2, 2, -2]
     
    queue = []
    queue.append(cell(knightpos[0], knightpos[1], 0))
    visited = [[False for i in range(N + 1)]
                      for j in range(N + 1)]
    visited[knightpos[0]][knightpos[1]] = True
    while(len(queue) > 0):
         
        t = queue[0]
        queue.pop(0)
        if(t.x == targetpos[0] and
           t.y == targetpos[1]):
            return t.dist
             
        # iterate for all reachable states
        for i in range(8):
             
            x = t.x + dx[i]
            y = t.y + dy[i]
             
            if(isInside(x, y, N) and not visited[x][y]):
                visited[x][y] = True
                queue.append(cell(x, y, t.dist + 1))
     
    
if __name__=='__main__':
    N = 30
    knightpos = [1, 1]
    targetpos = [30, 30]
    print(minStepToReachTarget(knightpos,
                               targetpos, N))
```

## Output:

![image](https://github.com/user-attachments/assets/4d4c30ba-3395-4bbc-9730-c870b28a3480)


## Result:
The program executed successfully, and the minimum number of steps for the knight to reach the target was calculated.
