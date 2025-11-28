https://www.geeksforgeeks.org/problems/detect-cycle-in-a-directed-graph/1
###### DFS Approach
```
class Solution {
  public:
    vector<vector<int>> make_graph(int V, vector<vector<int>> &edges){
        vector<vector<int>> graph(V);
        for(int i=0; i < edges.size(); i++)
            graph[edges[i][0]].push_back(edges[i][1]);
        
        return graph;
    }
    
    bool dfs_check(int node,vector<vector<int>>& graph,
				   vector<bool>& vis,vector<bool>& rec){
        
        vis[node] = true;
        rec[node] = true;
        
        for(auto child : graph[node]){
            if(vis[child] == false){
                if(dfs_check(child,graph,vis,rec))
                    return true;
            }
            else if(rec[child] == true)
                return true;
        }
        
        rec[node] = false;
        return false;
    }
    
    bool isCyclic(int V, vector<vector<int>> &edges) {
        vector<vector<int>> graph = make_graph(V,edges);
        
        vector<bool> vis(V,false);
        vector<bool> rec(V,false);
        
        for(int i=0; i < V; i++){
            if(vis[i] == false){
                if(dfs_check(i,graph,vis,rec))
                    return true;
            }
        }
        return false;
    }
};
```

###### BFS Approach
The BFS approach of finding whether cycle exists or not in a directed graph is done by Kahn's Algorithm in Topological sort.
[[BFS Approach of Cycle Detection of Directed Graph]]

Return -> [[Based on BFS-DFS Traversals]]

