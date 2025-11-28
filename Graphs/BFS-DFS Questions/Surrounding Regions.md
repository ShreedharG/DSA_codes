https://leetcode.com/problems/surrounded-regions/description/

```
class Solution {
public:
    void dfs(int row,int col,vector<vector<bool>>& vis,vector<vector<char>>& board,vector<int>& dx,vector<int>& dy,int m,int n){
      
        vis[row][col] = true;
        
        for(int k=0; k<4; k++){
            int nr = row + dx[k];
            int nc = col + dy[k];
  
            if(nr>=0 && nc>=0 && nr<m && nc<n && 
	           board[nr][nc]=='O' && !vis[nr][nc])
                dfs(nr,nc,vis,board,dx,dy);
        }
    }

    void solve(vector<vector<char>>& board){
        int m = board.size();
        int n = board[0].size();
  
        vector<vector<bool>> vis(m,vector<bool>(n,false));
        vector<int> dx = {-1,1,0,0};
        vector<int> dy = {0,0,-1,1};

        for(int j=0;j<n;j++){
            if(!vis[0][j] && board[0][j]=='O')
                dfs(0,j,vis,board,dx,dy,m,n);
                
            if(!vis[m-1][j] && board[m-1][j]=='O')
                dfs(m-1,j,vis,board,dx,dy,m,n);
        }
  
        for(int i=0;i<m;i++){
            if(!vis[i][0] && board[i][0]=='O')
                dfs(i,0,vis,board,dx,dy,m,n);
                
            if(!vis[i][n-1] && board[i][n-1]=='O')
                dfs(i,n-1,vis,board,dx,dy,m,n);
        }
  
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(!vis[i][j] && board[i][j] == 'O')
                    board[i][j] = 'X';
            }
        }
    }
};
```

Return -> [[Based on BFS-DFS Traversals]]

