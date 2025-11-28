https://www.geeksforgeeks.org/problems/steps-by-knight5927/1

```
class Solution {
  public:
    bool isInBoard(int ni,int nj,int n){
        if(ni>=0 && nj>=0 && ni<n && nj<n)
            return true;
        return false;
    }
    
    int minStepToReachTarget(vector<int>& knightPos,vector<int>& targetPos, int n){
        if(knightPos == targetPos) return 0;
        
        vector<int> dx = {1,-1,1,-1,2,2,-2, -2};
        vector<int> dy = {2,2,-2,-2,1,-1,1,-1};
        
        knightPos[0]--;knightPos[1]--;
        targetPos[0]--;targetPos[1]--;
        
        vector<vector<bool>> vis(n,vector<bool>(n,false));
        queue<pair<pair<int,int>,int>> q;
        
        vis[knightPos[0]][knightPos[1]] = true;
        q.push({{knightPos[0],knightPos[1]},0});
        
        while(!q.empty()){
            int i = q.front().first.first;
            int j = q.front().first.second;
            int steps = q.front().second;
            q.pop();
            
            for(int k=0;k<8;k++){
                int ni = i + dx[k];
                int nj = j + dy[k];
                
                if(isInBoard(ni,nj,n) && !vis[ni][nj]){
                    if(ni == targetPos[0] && nj == targetPos[1])
                        return (steps+1);
                    q.push({{ni,nj},steps+1});
                    vis[ni][nj] = true;
                }
            }
        }        
        return -1;
    }
};
```

Return -> [[Based on BFS-DFS Traversals]]

