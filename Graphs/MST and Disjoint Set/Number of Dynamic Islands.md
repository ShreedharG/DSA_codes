

```
class DSU{
private:
    vector<int> parent;
    vector<int> rank;
public:
    DSU(int total) {
        rank.resize(total,0);
        
        parent.resize(total);
        for(int i=0; i < total; i++)
            parent[i] = i;
    }
    
    int find(int x){
        if(x == parent[x])
            return x;
        
        return (parent[x] = find(parent[x]));
    }
    
    void union_(int x,int y){
        int px = find(x), py = find(y);
        
        if(px != py){
            if(rank[px] > rank[py]) parent[py] = px;
            else if(rank[px] < rank[py]) parent[px] = py;
            else{
                rank[px]++;
                parent[py] = px;
            }
        }
    }
};

class Solution {
  public:
    bool inBoard(int newR,int newC, int n,int m){
        return (newR>=0 && newC>=0 && newR<n && newC<m);
    }
    
    vector<int> numOfIslands(int n, int m, vector<vector<int>> &operators){
        int num_islands = 0;
        
        DSU dsu(n*m);
        
        vector<int> result;
        vector<vector<int>> vis(n, vector<int>(m, 0));
        vector<int> dx = {-1,1,0,0};
        vector<int> dy = {0,0,-1,1};
        
        for(auto& coordi : operators){            
            int row = coordi[0];
            int col = coordi[1];
            
            if(vis[row][col]){
                result.push_back(num_islands);
                continue;
            }
            
            vis[row][col] = 1;
            num_islands++;
                       
            for(int it=0; it < 4; it++){
                int newR = row + dx[it];
                int newC = col + dy[it];
                
                if(inBoard(newR,newC,n,m) && vis[newR][newC]){
                    int newIndex = newR*m + newC;
                    int index = coordi[0]*m + coordi[1];
                    
                    if(dsu.find(index) != dsu.find(newIndex)){
                        dsu.union_(index,newIndex);
                        num_islands--;
                    }
                }
            }
            result.push_back(num_islands);
        }
        return result;
    }
};
```

Return -> [[MST and Disjoint Set Problems]]

