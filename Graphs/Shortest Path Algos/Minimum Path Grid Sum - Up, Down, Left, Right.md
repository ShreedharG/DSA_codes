https://www.geeksforgeeks.org/problems/minimum-cost-path3833/1

```
class Solution {
  public:
    bool inBoard(int ni,int nj,int n){
        return (ni>=0 && nj>=0 && ni<n && nj<n);
    }
    
    int minimumCostPath(vector<vector<int>>& grid){
        int n = grid.size();
        vector<vector<int>> vis(n,vector<int>(n,INT_MAX));
        vector<int> dx = {0,0,1,-1};
        vector<int> dy = {1,-1,0,0};
    
        priority_queue<
            pair<int,pair<int,int>>,
            vector<pair<int,pair<int,int>>>,
            greater<pair<int,pair<int,int>>>
        > pq;
        
        pq.push({grid[0][0],{0,0}});
        vis[0][0] = grid[0][0];
        
        while(!pq.empty()){
            auto [cost,cell] = pq.top();
            int i = cell.first, j = cell.second;
            pq.pop();

            if(i==n-1 && j==n-1) return cost;
            
            if(cost > vis[i][j]) continue;
            
            for(int k=0;k<4;k++){
                int ni = i + dx[k];
                int nj = j + dy[k];
                
                if(inBoard(ni,nj,n) && vis[ni][nj] > cost+grid[ni][nj]){
                    pq.push({cost+grid[ni][nj],{ni,nj}});
                    vis[ni][nj] = cost+grid[ni][nj];
                }
            }
        }
        return -1;
    }
};
```

Return -> [[Shortest Path Algorithms]]

