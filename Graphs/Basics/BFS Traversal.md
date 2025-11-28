https://www.geeksforgeeks.org/problems/bfs-traversal-of-graph/1

```
class Solution {
  public:
    vector<int> bfs(vector<vector<int>> &adj){
        int n = adj.size();
        vector<int> bfs_trav;
        queue<int> q;
        
        vector<bool> visited(n,false);
        visited[0] = true;
        
        q.push(0);
        while(!q.empty()){
            int node = q.front();
            q.pop();
            bfs_trav.push_back(node);
            
            for(auto neighbour : adj[node]){
                if(visited[neighbour]==false){
                    visited[neighbour] = true;
                    q.push(neighbour);
                }
            }
        }
        return bfs_trav;
    }
};
```

Return -> [[Learning]]

