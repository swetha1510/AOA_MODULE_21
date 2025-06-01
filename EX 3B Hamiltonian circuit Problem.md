# EX 3B Hamiltonian Circuit Problem
## DATE:
## AIM:
To write a python program to check whether Hamiltonian path exits in the given graph.

## Algorithm
1.Start with a path list, which keeps track of the order of visited vertices.

2.Initialize the first position in the path to vertex 0.

3.Use a recursive helper function (hamUtil) to build the path one vertex at a time.

4.Try every possible vertex as the next move.

5.For each vertex v, check if it's a valid move.

6.It must be connected to the previous vertex (adj[path[pos-1]][v] == 1).

7.It must not have been visited before (v not in path).

8.If a vertex is valid:Place it in the path.

9.Move to the next position (pos+1) and continue recursively.

10.If you reach a position equal to the number of vertices (pos == N):

11.You’ve found a valid Hamiltonian Path — return True.

12.If no valid path is found from a position, backtrack:

13.Remove the vertex from the path (path[pos] = -1) and try the next one.

14.If the recursion completes and no path is found, return False.

## Program:
```
# Developed by: SWETHA P
# Register Number: 212222100053

def is_valid(v,pos,path,adj,N):
    
    if adj[path[pos-1]][v]==0:
        return False
    if v in path:
        return False
    return True
    
def hamUtil(adj,path,pos,N):
    if pos==N:
        return True
    for v in range(N):
        if is_valid(v,pos,path,adj,N):
            path[pos]=v
            if hamUtil(adj,path,pos+1,N):
                return True
            path[pos]=-1
            
def Hamiltonian_path(adj, N):
    path=[-1]*N
    path[0]=0

    if hamUtil(adj,path,1,N) == False:
        print ("Solution does not exist\n")
        return False

    # printSolution(path)
    return True
    
adj = [ [ 0, 1, 1, 1, 0 ] ,
        [ 1, 0, 1, 0, 1 ],
        [ 1, 1, 0, 1, 1 ],
        [ 1, 0, 1, 0, 0 ] ]
 
N = len(adj)
 
if (Hamiltonian_path(adj, N)):
    print("YES")
else:
    print("NO")
```

## Output:
![image](https://github.com/user-attachments/assets/cc1cc356-6700-4f8d-8b45-2190f721e89b)



## Result:
The Hamiltonian path program executed successfully, and it determined whether a Hamiltonian path exists in the given graph.
