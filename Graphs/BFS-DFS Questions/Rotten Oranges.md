https://leetcode.com/problems/rotting-oranges/

```
class Solution {
public:
    int orangesRotting(vector<vector<int>>& grid) {
        int m = grid.size();
        int n = grid[0].size();
        queue<pair<int,int>> q;

        // check for no fresh orange, and push all rotten
        int num_fresh = 0;
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(grid[i][j]==2) q.push({i,j});
                else if(grid[i][j]==1) num_fresh++;
            }
        }
        if(num_fresh==0) return 0;
        
        int time = 0;
        vector<int> dx = {1, -1, 0, 0};
        vector<int> dy = {0, 0, 1, -1};
  
        while(!q.empty()){
            int sz = q.size();
            time++;
            
            for(int it=0; it < sz; it++){
                auto [i,j] = q.front(); q.pop();

                for(int k=0;k<4;k++){
                    int ni = i+dx[k];
                    int nj = j+dy[k];

                    if(ni>=0 && nj>=0 && ni<m && nj<n && grid[ni][nj]==1){
                        grid[ni][nj] = 2;
                        num_fresh--;
                        q.push({ni,nj});
                    }
                }
            }
        }
  
        if(num_fresh>0) return -1;
        return time-1;
    }
};
```

Return -> [[Based on BFS-DFS Traversals]]

