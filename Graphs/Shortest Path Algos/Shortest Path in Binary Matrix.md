https://leetcode.com/problems/shortest-path-in-binary-matrix/

```
class Solution {
public:
    bool InBoard(int ni,int nj,int n){
        return (ni>=0 && ni<n && nj>=0 && nj<n);
    }
  
    int shortestPathBinaryMatrix(vector<vector<int>>& grid) {
        int n = grid.size();

        if(grid[0][0] == 1 || grid[n-1][n-1] == 1) return -1;
  
        vector<vector<int>> vis(n,vector<int>(n,INT_MAX));
        queue<pair<pair<int,int>,int>> q;
  
        vector<int> dx = {-1,-1,0,1,1,1,0,-1};
        vector<int> dy = {0,1,1,1,0,-1,-1,-1};
  
        q.push({{0,0},1});
        vis[0][0] = 1;

        while(!q.empty()){
            auto node = q.front();
            q.pop();
  
            int i = node.first.first;
            int j = node.first.second;
            int dis = node.second;
  
            for(int k=0;k<8;k++){
                int ni = i + dx[k];
                int nj = j + dy[k];
                if(InBoard(ni,nj,n) && grid[ni][nj]==0 && vis[ni][nj]>dis+1){
                    q.push({{ni,nj},dis+1});
                    vis[ni][nj] = dis+1;
                }
            }
        }

        return (vis[n-1][n-1] == INT_MAX) ? -1 : vis[n-1][n-1];
    }
};
```

Return -> [[Shortest Path Algorithms]]

