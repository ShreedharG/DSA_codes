https://leetcode.com/problems/island-perimeter/?envType=problem-list-v2&envId=array

```
class Solution {
public:
    int islandPerimeter(vector<vector<int>>& grid) {
        int n = grid.size();
        int m = grid[0].size();
        int perimeter = 0;
  
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j] == 1){
                    perimeter += 4;
                    if(i>0 && grid[i-1][j]) perimeter -= 2;
                    if(j>0 && grid[i][j-1]) perimeter -= 2;
                }
            }
        }
  
        return perimeter;
    }
};
```

Return -> [[Arrays, Prefix-Suffix, Hashing, Maps]]

