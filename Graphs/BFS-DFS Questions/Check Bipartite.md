https://www.geeksforgeeks.org/problems/bipartite-graph/1
###### BFS Approach
```
class Solution {
  public:
    bool isBipartite(int V, vector<vector<int>> &edges){
        vector<int> vis(V,-1);
        
        vector<vector<int>> graph(V);
        for(auto& e : edges){
            graph[e[0]].push_back(e[1]);
            graph[e[1]].push_back(e[0]);
        }
        
        queue<int> q;
        
        for(int i=0;i<V;i++){
            if(vis[i] == -1){
                q.push(i);
                vis[i] = 0;
                
                while(!q.empty()){
                    int node = q.front();
                    q.pop();
                    
                    for(auto neigh : graph[node]){
                        if(vis[neigh] == -1){
                            vis[neigh] = !vis[node];
                            q.push(neigh);
                        }
                        else if(vis[neigh] == vis[node])
                            return false;
                    }
                }
            }
        }
        return true;
    }
};
```

###### DFS Approach
```
class Solution {
  public:
    bool check_bipartite(int node,vector<int>& vis,vector<vector<int>>& adj){
        for(auto neigh : adj[node]){
            if(vis[neigh] == -1){
                vis[neigh] = !vis[node];
                if(!check_bipartite(neigh, vis, adj))
                    return false;
            }
            else if(vis[neigh] == vis[node])
                return false;
        }
        return true;
    }
    
    bool isBipartite(int V, vector<vector<int>> &edges){
        vector<int> vis(V,-1);
        
        vector<vector<int>> graph(V);
        for(auto& e : edges){
            graph[e[0]].push_back(e[1]);
            graph[e[1]].push_back(e[0]);
        }
        
        for(int i=0;i<V;i++){
            if(vis[i] == -1){
                vis[i] = 0;
                if(!check_bipartite(i,vis,graph))
                    return false;
            }
        }
        return true;
    }
};
```


Return -> [[Based on BFS-DFS Traversals]]

