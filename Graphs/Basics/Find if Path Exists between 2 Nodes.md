https://leetcode.com/problems/find-if-path-exists-in-graph/
###### BFS Approach
```
class Solution {
public:
    bool validPath(int n,vector<vector<int>>& edges,int source, int destination) {
        if(source == destination) return true;

        vector<vector<int>> adj(n);
        for(int i=0; i<edges.size(); i++){
            adj[edges[i][0]].push_back(edges[i][1]);
            adj[edges[i][1]].push_back(edges[i][0]);
        }
        vector<bool> vis(n);
  
        queue<int> q;
        q.push(source);
        vis[source] = true;
  
        while(!q.empty()){
            int node = q.front();
            q.pop();

            if(node == destination) return true;

            for(auto neigh : adj[node]){              
                if(vis[neigh] == false){
                    q.push(neigh);
                    vis[neigh] = true;
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
    bool dfs_traversal(int node,int dest,vector<vector<int>>& graph,vector<bool>& vis){
        if(node == dest) return true;

        vis[node] = true;
        for(auto child : graph[node]){
            if(vis[child] == false){
                if(dfs_traversal(child,dest,graph,vis))
                    return true;
            }          
        }
        return false;
    }

    bool validPath(int n,vector<vector<int>>& edges,int source, int destination) {
        if(source == destination) return true;

        vector<vector<int>> graph(n);
        for(int i=0; i<edges.size(); i++){
            graph[edges[i][0]].push_back(edges[i][1]);
            graph[edges[i][1]].push_back(edges[i][0]);
        }

        vector<bool> vis(n,false);
        return dfs_traversal(source,destination,graph,vis);
    }
};
```

Return -> [[Learning]]