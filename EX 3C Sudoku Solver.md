# EX 3C Sudoku Solver
## DATE:
## AIM:
To write a python program to find the solution of sudoku puzzle using Backtracking.


## Algorithm

1.Find an empty cell (a cell with value 0).

2.Use isEmpty() to scan the board and return the position of the first empty cell.

3.If no empty cell is found, the board is complete!

4.Call printBoard() to display the solved Sudoku.

5.If there is an empty cell:Try placing each number from 1 to 9 in that cell.

6.For each number:Check if placing it is allowed using isPossible():

7.The number should not already be in the same row.

8.It should not be in the same column.

9.It should not be in the same 3x3 subgrid.

10.If the number is allowed:Place it in the cell.

11.Recursively call solve() to fill the next empty cell.

12.If solve() returns True, you're done.

13.If solve() returns False, it means that guess led to a dead end.

14.So, reset the cell back to 0 and try the next number (this is backtracking).

15.Repeat this process until the board is fully and correctly filled.

## Program:
```
# Developed by: SWETHA P
# Register Number: 212222100053

board = [
    [0, 0, 0, 8, 0, 0, 4, 0, 3],
    [2, 0, 0, 0, 0, 4, 8, 9, 0],
    [0, 9, 0, 0, 0, 0, 0, 0, 2],
    [0, 0, 0, 0, 2, 9, 0, 1, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 7, 0, 6, 5, 0, 0, 0, 0],
    [9, 0, 0, 0, 0, 0, 0, 8, 0],
    [0, 6, 2, 7, 0, 0, 0, 0, 1],
    [4, 0, 3, 0, 0, 6, 0, 0, 0]
]

def printBoard(board):
    for i in range(0, 9):
        for j in range(0, 9):
            print(board[i][j], end=" ")
        print()

def isPossible(row, col, val):
    for j in range(0, 9):
        if board[row][j] == val:
            return False

    for i in range(0, 9):
        if board[i][col] == val:
            return False

    startRow = (row // 3) * 3
    startCol = (col // 3) * 3
    for i in range(0, 3):
        for j in range(0, 3):
            if board[startRow+i][startCol+j] == val:
                return False
    return True
def isEmpty():
    for r in range(9):
        for c in range(9):
            if board[r][c] == 0:
                return r, c
    return None

def solve():

    empty = isEmpty()
    if empty is None:
        printBoard(board)
        return True

    row, col = empty
    for guess in range(1, 10):
        if isPossible(row, col, guess):
            board[row][col] = guess
            if solve():
                return True
            board[row][col] = 0
    return False
solve()
```

## Output:
![image](https://github.com/user-attachments/assets/1d71442e-8317-43e3-a2ab-6d98f93537ec)


## Result:
The Sudoku solver program executed successfully and found the solution for the given puzzle.
