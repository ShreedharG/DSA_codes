https://leetcode.com/problems/number-of-operations-to-make-network-connected/
###### BFS-DFS Method
Can be solved using simple BFS-DFS traversal to find the number of connected components and use the answer to return number of connections required.
###### DSU Method
```
class DSU{
public:
    vector<int> rank;
    vector<int> parent;

    DSU(int n){
        rank.resize(n,0);
        parent.resize(n);
        for(int i=0;i<n;i++)
            parent[i] = i;
    }

    int find(int x){
        if(x == parent[x]) return x;
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
    int makeConnected(int n, vector<vector<int>>& connections) {
        int sz = connections.size();
        if(sz < n-1) return -1;
  
        DSU dsu(n);  
        for(auto wire : connections){
            int u = wire[0], v = wire[1];
  
            if(dsu.find(u) != dsu.find(v))
	            dsu.union_(u,v);
        }
  
        int components = 0;
        for(int i=0;i<n;i++)
            if(dsu.parent[i] == i) components++;

        return components-1;
    }
};
```

Return -> [[Based on BFS-DFS Traversals]], [[MST and Disjoint Set Problems]]

