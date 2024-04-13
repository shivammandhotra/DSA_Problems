
# Valid Sudoku

Determine if a 9 x 9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

Each row must contain the digits 1-9 without repetition.
Each column must contain the digits 1-9 without repetition.
Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.
Note:

A Sudoku board (partially filled) could be valid but is not necessarily solvable.
Only the filled cells need to be validated according to the mentioned rules.
 
```
Example 1:

Input: board = 
[["5","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]
Output: true

Example 2:

Input: board = 
[["8","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]
Output: false
Explanation: Same as Example 1, except with the 5 in the top left corner being modified to 8. Since there are two 8's in the top left 3x3 sub-box, it is invalid.
 
 
```

## Solution 

```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        for(int i=0;i<9;i++){
            HashSet<Character> rowSet = new HashSet<>();
            HashSet<Character> colSet = new HashSet<>();
            for(int j=0;j<9;j++){
                char r = board[i][j];
                char c = board[j][i];
                if(r!='.'){
                    if(rowSet.contains(r)){
                        return false;
                    }
                    else{
                        rowSet.add(r);
                    }
                }
                if(c!='.'){
                    if(colSet.contains(c)){
                        return false;
                    }
                    else{
                        colSet.add(c);
                    }
                }
            }
        }

        for(int i=0;i<9;i=i+3){
            for(int j=0;j<9;j=j+3){
                if(!checkBlock(i,j,board)){
                    return false;
                }
            }
        }
        return true;
    }

    public boolean checkBlock(int idxI,int idxJ, char[][] board){
        int rows = idxI+3;
        int cols = idxJ+3;
        HashSet<Character> blockSet = new HashSet<>();
        for(int i=idxI;i<rows;i++){
            for(int j=idxJ;j<cols;j++){
                char b = board[i][j];
                if(b=='.') continue;
                if(blockSet.contains(b)){
                    return false;
                }
                blockSet.add(b);
            }
        }
        return true;
    }
}
```

#### Space complexity : O(n)
#### Time complexity: O(n)
