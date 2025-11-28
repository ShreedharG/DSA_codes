https://www.geeksforgeeks.org/problems/number-of-distinct-islands/1
###### BFS Approach
```
class Solution {
  public:
    int countDistinctIslands(vector<vector<int>>& grid){
        set<vector<pair<int,int>>> disIslands;
        int n = grid.size();
        int m = grid[0].size();
        
        vector<vector<bool>> vis(n,vector<bool>(m,false));
        vector<int> dx = {-1,1,0,0};
        vector<int> dy = {0,0,-1,1};
        queue<pair<int,int>> q;
        
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j] == 1 && !vis[i][j]){
                    int rel_i = i;
                    int rel_j = j;
                    vector<pair<int,int>> combo = {};
                    
                    q.push({i,j});
                    vis[i][j] = true;
                    combo.push_back({0,0});
                    
                    while(!q.empty()){
                        int id1 = q.front().first;
                        int id2 = q.front().second;
                        q.pop();
                        
                        for(int k=0;k<4;k++){
                            int n1 = id1 + dx[k];
                            int n2 = id2 + dy[k];
                            
                            if(n1>=0 && n1<n && n2>=0 && n2<m && 
                               grid[n1][n2]==1 && !vis[n1][n2]){
                                   q.push({n1,n2});
                                   vis[n1][n2] = true;
                                   combo.push_back({n1-rel_i,n2-rel_j});
                               }
                                
                        }
                    }
                    if(!combo.empty())
                        disIslands.insert(combo);
                }
            }
        }
        return disIslands.size();
    }
};
```

Return -> [[Based on BFS-DFS Traversals]]

