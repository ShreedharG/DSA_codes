https://leetcode.com/problems/sudoku-solver/description/

```
class Solution {
public:
    bool isVal(int row,int col,vector<vector<char>>& board,char c){
        for(int i=0;i<board.size();i++){
            if(board[row][i]==c) return false;
            if(board[i][col]==c) return false;

            if(board[(row/3)*3 + (i/3)][(col/3)*3 + (i%3)]==c) return false;
        }
        return true;
    }

    bool solve(vector<vector<char>>& board){
        for(int i=0;i<board.size();i++){
            for(int j=0;j<board[0].size();j++){
                if(board[i][j]=='.'){
                    for(char c = '1';c<='9';c++){
                        if(isVal(i,j,board,c)){
                            board[i][j] = c;
                            if(solve(board)==true)
                                return true;
                            else
                                board[i][j] = '.';
                        }
                    }
                    return false;                    
                }
            }
        }
        return true;
    }

    void solveSudoku(vector<vector<char>>& board) {
        solve(board);        
    }
};
```

Return -> [[Recursion + Backtracking]]
