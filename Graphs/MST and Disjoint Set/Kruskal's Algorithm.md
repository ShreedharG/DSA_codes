https://www.geeksforgeeks.org/problems/minimum-spanning-tree-kruskals-algorithm/1

```
class DSU{
private:
    vector<int> rank;
    vector<int> parent;
public:
    DSU(int n){
        rank.resize(n,0);
        parent.resize(n);
        for(int i=0;i<n;i++)
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
    static bool compare(vector<int> edge1, vector<int> edge2){
        return edge1[2] < edge2[2];
    }
    
    int kruskalsMST(int V, vector<vector<int>> &edges) {
        DSU dsu(V);
        int sum = 0;
        
        sort(edges.begin(),edges.end(),compare);
        
        for(auto edge : edges){
            int u = edge[0], v = edge[1];
            int pu = dsu.find(u), pv = dsu.find(v);
            
            if(pu != pv){
                sum += edge[2];
                dsu.union_(u,v);
            }
        }
        return sum;
    }
};
```

Return -> [[MST and Disjoint Set Problems]]

