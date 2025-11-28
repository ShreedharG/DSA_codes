https://leetcode.com/problems/flood-fill/
###### BFS Approach
```
class Solution {
public:
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int color) {
        int m = image.size();
        int n = image[0].size();
  
        if(image[sr][sc] == color) return image;
  
        int o_col = image[sr][sc];
  
        vector<int> dx = {-1,1,0,0};
        vector<int> dy = {0,0,-1,1};
        queue<pair<int,int>> q;

        image[sr][sc] = color;
        q.push({sr,sc});

        while(!q.empty()){
            int i = q.front().first;
            int j = q.front().second;
            q.pop();
  
            for(int k=0;k<4;k++){
                int ni = i + dx[k];
                int nj = j + dy[k];


                if(ni>=0 && ni<m && nj>=0 && nj<n && image[ni][nj]==o_col){
                    q.push({ni,nj});
                    image[ni][nj] = color;
                }
            }
        }
        return image;
    }
};
```

Return -> [[Based on BFS-DFS Traversals]]

