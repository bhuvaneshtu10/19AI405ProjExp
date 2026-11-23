## Sudoku Solver Using Backtracking Algorithm
## 1. Project Overview

This project implements a Sudoku Solver using the Backtracking Algorithm in Python. Sudoku is a logic-based number puzzle in which a 9×9 grid must be filled with digits from 1 to 9 while satisfying specific rules.

The main objective of this project is to solve a given Sudoku puzzle automatically using recursion and backtracking techniques.

## 2. Objectives
To understand the concept of the Backtracking Algorithm.
To implement an efficient Sudoku-solving program using Python.
To apply recursion to solve constraint-satisfaction problems.
To validate Sudoku rules before inserting numbers.
To find a valid solution for a given Sudoku puzzle.
## 3. Technologies Used
Programming Language: Python 3
Algorithm: Backtracking
Concepts: Recursion, Constraint Satisfaction, Depth-First Search
IDE: Python IDLE / Visual Studio Code
## 4. Sudoku Rules

A Sudoku puzzle consists of a 9×9 grid divided into nine 3×3 subgrids.

The following rules must be satisfied:

Each row must contain digits from 1 to 9 without repetition.
Each column must contain digits from 1 to 9 without repetition.
Each 3×3 subgrid must contain digits from 1 to 9 without repetition.

In this program, 0 represents an empty cell.

## 5. Algorithm Used – Backtracking

Backtracking is a recursive algorithmic technique that builds a solution step by step.

Steps:
Find an empty cell in the Sudoku grid.
Try inserting numbers from 1 to 9.
Check whether the selected number satisfies Sudoku rules.
If the number is valid, place it in the cell.
Recursively solve the remaining empty cells.
If no valid solution is found, remove the previously inserted number.
Repeat until the Sudoku puzzle is completely solved.


## 6. How to Run the Program
Prerequisites
Python 3 must be installed on your system.
A Python-supported IDE or terminal.
Execution Steps
Clone the repository:
bash
git clone https://github.com/natsaravanan/19AI405ProjExp.git

Navigate to the project directory:
bash
cd 19AI405ProjExp

Run the Python program:
bash
python sudokunew.py

The program displays the solved Sudoku puzzle if a solution exists.

## 7. Program

```
M = 9
def print_puzzle(grid):
    for row in grid:
        print(" ".join(map(str, row)))
def is_safe(grid, row, col, num):
    for x in range(9):
        if grid[row][x] == num:
            return False
    for x in range(9):
        if grid[x][col] == num:
            return False
    start_row = row - row % 3
    start_col = col - col % 3
    for i in range(3):
        for j in range(3):
            if grid[start_row + i][start_col + j] == num:
                return False
    return True
def solve_sudoku(grid, row=0, col=0):
    if row == 9:
        return True
    if col == 9:
        return solve_sudoku(grid, row + 1, 0)
    if grid[row][col] != 0:
        return solve_sudoku(grid, row, col + 1)
    for num in range(1, 10):
        if is_safe(grid, row, col, num):
            grid[row][col] = num
            if solve_sudoku(grid, row, col + 1):
                return True
            grid[row][col] = 0
    return False
grid = [
    [2, 5, 0, 0, 3, 0, 9, 0, 1],
    [0, 1, 0, 0, 0, 4, 0, 0, 0],
    [4, 0, 7, 0, 0, 0, 2, 0, 8],
    [0, 0, 5, 2, 0, 0, 0, 0, 0],
    [0, 0, 0, 0, 9, 8, 1, 0, 0],
    [0, 4, 0, 0, 0, 3, 0, 0, 0],
    [0, 0, 0, 3, 6, 0, 0, 7, 2],
    [0, 7, 0, 0, 0, 0, 0, 0, 3],
    [9, 0, 3, 0, 0, 0, 6, 0, 4]
]
if solve_sudoku(grid):
    print("Sudoku Solution:")
    print_puzzle(grid)
else:
    print("No solution exists")
```

## 8. Sample Input

The Sudoku puzzle is represented using a 9×9 matrix.

text
2 5 0 0 3 0 9 0 1
0 1 0 0 0 4 0 0 0
4 0 7 0 0 0 2 0 8
0 0 5 2 0 0 0 0 0
0 0 0 0 9 8 1 0 0
0 4 0 0 0 3 0 0 0
0 0 0 3 6 0 0 7 2
0 7 0 0 0 0 0 0 3
9 0 3 0 0 0 6 0 4

## 9. Expected Output

The program displays the completed Sudoku grid after successfully applying the Backtracking Algorithm.

text
Sudoku Solution:
[The completed 9×9 Sudoku grid]


If no valid solution exists, the program displays:

text
No solution exists

## 10. Functions Used
Function	Description
print_puzzle()	Displays the Sudoku grid.
is_safe()	Checks whether a number can be placed in a particular cell.
solve_sudoku()	Solves the Sudoku puzzle using recursion and backtracking.
## 11. Time and Space Complexity

Let n represent the number of empty cells in the Sudoku grid.

Time Complexity: O(9ⁿ) in the worst case, as each empty cell can potentially have nine possible values.
Space Complexity: O(n) for the recursive call stack.

The actual execution time depends on the number of empty cells and the constraints of the given Sudoku puzzle.

## 12. Applications
Artificial Intelligence and search algorithms.
Constraint Satisfaction Problems (CSP).
Puzzle-solving applications.
Recursive problem-solving techniques.
Combinatorial optimization.
## 13. Advantages
Automatically solves Sudoku puzzles.
Uses systematic search to find a valid solution.
Demonstrates recursion and backtracking.
Avoids invalid number placements by checking constraints.
Can solve different Sudoku puzzles by changing the input grid.

## 14. Output

<img width="1441" height="717" alt="Screenshot 2026-11-23 194036" src="https://github.com/user-attachments/assets/e2646b93-0212-44b3-af27-53e33842f890" />

## 15. Conclusion

The Sudoku Solver project demonstrates the practical implementation of the Backtracking Algorithm using Python. By checking constraints and exploring possible number combinations, the program can solve Sudoku puzzles systematically.

This project provides a clear understanding of recursion, search techniques, and constraint-satisfaction problems in Artificial Intelligence.
