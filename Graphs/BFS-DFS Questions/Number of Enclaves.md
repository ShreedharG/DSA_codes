https://leetcode.com/problems/number-of-enclaves/
###### DFS Approach
```
class Solution {
public:
    void dfs(int r,int c,vector<vector<int>>& grid,vector<vector<bool>>& vis,int m,int n,vector<int>& dx,vector<int>& dy){
        
        vis[r][c] = true;
        for(int k=0;k<4;k++){
            int nr = r + dx[k];
            int nc = c + dy[k];
            
            if(nr>=0 && nr<m && nc>=0 && nc<n && 
	           !vis[nr][nc] && grid[nr][nc]==1)
                dfs(nr,nc,grid,vis,m,n,dx,dy);
        }
    }
 
    int numEnclaves(vector<vector<int>>& grid) {
        int m = grid.size();
        int n = grid[0].size();
  
        vector<vector<bool>> vis(m,vector<bool>(n,false));
        vector<int> dx = {-1,1,0,0};
        vector<int> dy = {0,0,-1,1};
  
        for(int i=0;i<m;i++){
            if(grid[i][0] == 1 && !vis[i][0])
                dfs(i,0,grid,vis,m,n,dx,dy);
                
            if(grid[i][n-1] == 1 && !vis[i][n-1])
                dfs(i,n-1,grid,vis,m,n,dx,dy);
        }
  
        for(int j=0;j<n;j++){
            if(grid[0][j] == 1 && !vis[0][j])
                dfs(0,j,grid,vis,m,n,dx,dy);
                
            if(grid[m-1][j] == 1 && !vis[m-1][j])
                dfs(m-1,j,grid,vis,m,n,dx,dy);
        }
  
        int count = 0;
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(grid[i][j] == 1 && !vis[i][j])
                    count++;
            }
        }  
        return count;
    }
};
```

Return -> [[Based on BFS-DFS Traversals]]

