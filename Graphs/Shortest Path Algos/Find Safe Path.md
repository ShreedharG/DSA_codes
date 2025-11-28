https://leetcode.com/problems/find-a-safe-walk-through-a-grid/?envType=problem-list-v2&envId=shortest-path

```
class Solution {
public:
    bool findSafeWalk(vector<vector<int>>& grid, int health) {
        int n = grid.size();
        int m = grid[0].size();
  
        vector<vector<int>> maxHealth(n,vector<int>(m,0));
        priority_queue<pair<int,pair<int,int>>> pq;
  
        int dx[] = {0,0,-1,1};
        int dy[] = {1,-1,0,0};

        int startHealth = health -grid[0][0];
        if (startHealth < 1) return false;
  
        maxHealth[0][0] = startHealth;
        pq.push({startHealth, {0, 0}});
  
        while(!pq.empty()){
            auto [currHealth, pos] = pq.top();
            int i = pos.first;
            int j = pos.second;
            pq.pop();
  
            if(currHealth < maxHealth[i][j]) continue;
            if(currHealth < 1) continue;
            if(i == n-1 && j == m-1) return true;
  
            for(int k=0;k<4;k++){
                int ni = i + dx[k];
                int nj = j + dy[k];
  
                if(ni>=0 && nj>=0 && ni<n && nj<m){
                    int newHealth = currHealth - grid[ni][nj];
                    if(newHealth > 0 && newHealth > maxHealth[ni][nj]){
                        maxHealth[ni][nj] = newHealth;
                        pq.push({newHealth,{ni,nj}});
                    }
                }
            }
        }
        return false;
    }
};
```

Return -> [[Shortest Path Algorithms]]

