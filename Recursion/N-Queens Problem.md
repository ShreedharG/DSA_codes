https://leetcode.com/problems/n-queens/
###### Check every time
```
class Solution {
public:
    bool isSafe(int row,int col,vector<string> &board,int n){
        int r = row;int c = col;     
        while(r>=0 && c>=0){
            if(board[r][c]=='Q')
                return false;
            r--;
            c--;
        } 

        r=row;c=col;        
        while(c>=0){
            if(board[r][c]=='Q')
                return false;
            c--;
        }
        
        r=row;c=col;        
        while(c>=0 && r<n){
            if(board[r][c]=='Q')
                return false;
            c--;
            r++;          
        }
        
        return true;
    }

    void solve(int c,vector<string> &board,vector<vector<string>> &ans,int n){
        if(c==n){
            ans.push_back(board);
            return;
        }

        for(int row=0;row<n;row++){
            if(isSafe(row,c,board,n)){
                board[row][c] = 'Q';
                solve(c+1,board,ans,n);
                board[row][c] = '.';
            }
        }
    }

    vector<vector<string>> solveNQueens(int n) {
        vector<vector<string>> ans;
        string s(n ,'.');
        vector<string> board(n);

        for(int i=0;i<n;i++)
            board[i] = s;
        solve(0,board,ans,n);
        return ans;
    }
};
```

###### The 2nd approach makes use of arrays to store places already having a value
```
class Solution {
public:
    void solve(int col,vector<string> &board,vector<vector<string>> &ans,vector<int>& leftRow,vector<int>& upperDiagnol,vector<int>& lowerDiagnol,int n){
        if(col==n){
            ans.push_back(board);
            return;
        }  

        for(int row=0;row<n;row++){
            if(leftRow[row]==0 && upperDiagnol[n-1-(row-col)]==0 && lowerDiagnol[row+col]==0){
                board[row][col] = 'Q';
                leftRow[row] = 1;
                upperDiagnol[n-1-(row-col)] = 1;
                lowerDiagnol[row+col] = 1;

                solve(col+1,board,ans,leftRow,upperDiagnol,lowerDiagnol,n);

                board[row][col] = '.';
                leftRow[row] = 0;
                upperDiagnol[n-1-(row-col)] = 0;
                lowerDiagnol[row+col] = 0;
            }
        }
    }  

    vector<vector<string>> solveNQueens(int n) {
        vector<vector<string>> ans;
        string s(n ,'.');
        vector<string> board(n);
  
        vector<int> leftRow(n,0);
        vector<int> upperDiagnol(2*n-1,0);
        vector<int> lowerDiagnol(2*n-1,0);  

        for(int i=0;i<n;i++)
            board[i] = s;
            
        solve(0,board,ans,leftRow,upperDiagnol,lowerDiagnol,n);
        return ans;
    }
};
```

Return -> [[Recursion + Backtracking]]