https://leetcode.com/problems/making-a-large-island/
###### Using Union by Size
```
class Solution {
public:
  bool inBoard(int ni,int nj,int n){
    return (ni>=0 && nj>=0 && ni<n && nj<n);
  }
  
  int largestIsland(vector<vector<int>>& grid) {
    int n = grid.size();
    DSU dsu(n*n);

    vector<int> dx = {-1,1,0,0};
    vector<int> dy = {0,0,-1,1};

    int num_ones = 0;

    for(int i=0;i<n;i++){
      for(int j=0;j<n;j++){
        if(grid[i][j] == 1){
          num_ones++;
          for(int k=0;k<4;k++){
            int ni = i + dx[k];
            int nj = j + dy[k];  

            if(inBoard(ni,nj,n) && grid[ni][nj]==1){
              int index = i*n + j;
              int newIndex = ni*n + nj;
              dsu.union_(index,newIndex);
            }
          }
        }
      }
    }

    if(num_ones == n*n) return num_ones;

    int max_area = 1;
    for(int i=0;i<n;i++){
      for(int j=0;j<n;j++){
        if(grid[i][j]==0){
          int area = 1;
          set<int> adjComponents;
          
          for(int k=0;k<4;k++){
            int ni = i + dx[k];
            int nj = j + dy[k];
            int newIndex = ni*n + nj;

            if(inBoard(ni,nj,n) && grid[ni][nj]==1)
              adjComponents.insert(dsu.find(newIndex));
          }
          
          for(auto it : adjComponents) 
	          area += dsu.getSize(it);
          max_area = max(max_area,area);
        }
      }
    }
    return max_area;
  }
};
```

Return -> [[MST and Disjoint Set Problems]]

