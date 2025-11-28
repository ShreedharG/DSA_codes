https://leetcode.com/problems/01-matrix/

```
class Solution {
public:
    bool isInBoard(int i,int j,int m,int n){
        return (i>=0 && i<m && j>=0 && j<n);
    }  

    vector<vector<int>> updateMatrix(vector<vector<int>>& mat){
        int m = mat.size();
        int n = mat[0].size();

        vector<int> dx = {-1,1,0,0};
        vector<int> dy = {0,0,-1,1};
  
        vector<vector<bool>> vis(m,vector<bool>(n,false));
        queue<pair<int,int>> q;
  
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(mat[i][j] == 0){
                    q.push({i,j});
                    vis[i][j] = true;
                }
            }
        }
  
        while(!q.empty()){
            int i = q.front().first;
            int j = q.front().second;
            q.pop();
  
            for(int k=0;k<4;k++){
                int ni = i + dx[k];
                int nj = j + dy[k];

                if(isInBoard(ni,nj,m,n) && !vis[ni][nj]){
                    vis[ni][nj] = true;
                    mat[ni][nj] = mat[i][j] + 1;
                    q.push({ni,nj});
                }
            }
        }
        return mat;
    }
};
```

Return -> [[Based on BFS-DFS Traversals]]

