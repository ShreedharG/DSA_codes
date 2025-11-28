https://leetcode.com/problems/number-of-islands/

```
class Solution {
public:
	bool inBoard(int ni,int nj,int n,int m){
        return (ni>=0 && nj>=0 && ni<n && nj<m);
    }
    
    int numIslands(vector<vector<char>>& grid) {
        int n = grid.size();
        int m = grid[0].size();
  
        vector<vector<bool>> vis(m,vector<bool>(n,false));
        queue<pair<int,int>> q;
        int count = 0;

        vector<int> dx = {-1,1,0,0};
        vector<int> dy = {0,0,-1,1};  

        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j]=='1' && !vis[i][j]){
                    count++;
                    q.push({i,j});
                    vis[i][j] = true;

                    while(!q.empty()){
                        auto[i,j] = q.front();
                        q.pop();
                        
                        for(int k=0; k<4; k++){
                            int ni = i + dx[k];
                            int nj = j + dy[k];

                            if(inBoard(ni,nj,n,m) && grid[ni][nj]=='1'
	                            && !vis[ni][nj]){
                                vis[ni][nj] = true;
                                q.push({ni,nj});
                            }
                        }
                    }
                }
            }
        }
        return count;
    }
};
```

Return -> [[Based on BFS-DFS Traversals]]

