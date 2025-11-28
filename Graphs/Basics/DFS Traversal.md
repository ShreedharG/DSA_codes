https://www.geeksforgeeks.org/problems/depth-first-traversal-for-a-graph/1

```
class Solution {
  public:
    void dfs_t(int node,vector<int>& res,vector<bool>& vis,vector<vector<int>>& adj){
        res.push_back(node);
        vis[node] = true;
        
        for(int i=0; i < adj[node].size(); i++){
            if(vis[(adj[node][i])]==false)
                dfs_t(adj[node][i],res,vis,adj);
        }
    }
    
    vector<int> dfs(vector<vector<int>>& adj){
        vector<int> result;
        int n = adj.size();
        
        vector<bool> vis(n,false);
        vis[0] = true;
        
        dfs_t(0,result,vis,adj);
        return res;
    }
};
```

Return -> [[Learning]]

