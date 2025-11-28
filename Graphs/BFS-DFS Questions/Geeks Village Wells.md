https://www.geeksforgeeks.org/problems/geeks-village-and-wells--170647/1

```
class Solution {
  public:
    bool inBoard(int ni,int nj,int n,int m){
        return (ni>=0 && nj>=0 && ni<n && nj<m);
    }    
    
    vector<vector<int>> chefAndWells(int n, int m, vector<vector<char>> &c){
        vector<vector<int>> dis(n,vector<int>(m,-1));
        queue<pair<int,int>> q;
        vector<int> dx = {-1,1,0,0}, dy = {0,0,-1,1};
        
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(c[i][j] == 'W'){
                    q.push({i,j});
                    dis[i][j] = 0;
                }
                else if(c[i][j] == 'N')
                    dis[i][j] = 0;
            }
        }
        
        while(!q.empty()){
            auto [i,j] = q.front();
            q.pop();
            
            for(int k=0;k<4;k++){
                int ni = i + dx[k], nj = j + dy[k];
                if(inBoard(ni,nj,n,m) && dis[ni][nj] == -1){
					dis[ni][nj] = 2 + dis[i][j];
					q.push({ni,nj});
                }
            }
        }
        
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(c[i][j] == '.')
                    dis[i][j] = 0;
            }
        }        
        return dis;
    }
};
```

Return -> [[Based on BFS-DFS Traversals]]

