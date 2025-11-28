https://www.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1
###### BFS Approach
```
class Solution {
  public:    
    bool isCycle(int V, vector<vector<int>>& edges){
        vector<bool> vis(V,false);
        vector<vector<int>> graph(V);
        for(auto e : edges){
            int u = e[0], v = e[1];
            
            graph[u].push_back(v);
            graph[v].push_back(u);
        }
        
        for(int i=0;i<V;i++){
            if(!vis[i]){
                queue<pair<int,int>> q;
                q.push({i,-1});
                vis[i] = true;
                
                while(!q.empty()){
                    auto [node,parent] = q.front();
                    q.pop();
                    
                    for(auto neigh : graph[node]){
                        if(!vis[neigh]){
                            vis[neigh] = true;
                            q.push({neigh,node});
                        }
                        else if(neigh != parent)
                            return true;
                    }
                }
            }
        }
        return false;
    }
};
```

###### DFS Approach
```
class Solution {
  public:
    bool dfs_trav(int node,int parent,vector<bool>& vis,vector<vector<int>>& graph){
        vis[node] = true;
        
        for(auto child : graph[node]){
            if(!vis[child]){
                if(dfs_trav(child,node,vis,graph))
                    return true;
            }
            else if(child != parent)
                return true;
        }
        return false;
    }
    
    bool isCycle(int V, vector<vector<int>>& edges){
        vector<bool> vis(V,false);
        vector<vector<int>> graph(V);
        for(auto e : edges){
            int u = e[0], v = e[1];
            
            graph[u].push_back(v);
            graph[v].push_back(u);
        }
        
        for(int i=0;i<V;i++){
            if(!vis[i]){
                if(dfs_trav(i,-1,vis,graph))
                    return true;
            }
        }
        return false;
    }
};
```

###### Using DSU Data Structure
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
    bool isCycle(int V, vector<vector<int>>& edges) {
        DSU dsu(V);
        for(auto edge : edges){
            int u = edge[0], v = edge[1];
            int p1 = dsu.find(u), p2 = dsu.find(v);
            
            if(s1 == s2) return true;
            
            dsu.union_(u,v);
        }
        return false;
    }
};
```


Return -> [[Based on BFS-DFS Traversals]] , [[MST and Disjoint Set Problems]]

