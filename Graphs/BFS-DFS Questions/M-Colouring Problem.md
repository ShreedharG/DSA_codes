https://www.geeksforgeeks.org/problems/m-coloring-problem-1587115620/1

```
class Solution {
  public:
    bool isSafe(int node,int color,vector<vector<int>>& gr,vector<int>& col){
        for(auto neigh : gr[node]){
            if(col[neigh] == color)
                return false;
        }
        
        return true;
    }
    
    bool solve(int node,vector<int>& col,vector<vector<int>>& gr,int v,int m){
        if(node == v) return true;
        
        for(int c = 0; c < m; c++){
            if(isSafe(node,c,gr,col)){
                col[node] = c;
                
                if(solve(node+1,col,gr,v,m))
                    return true;
                
                col[node] = -1;
            }
        }
        
        return false;
    }
    
    bool graphColoring(int v, vector<vector<int>> &edges, int m){
        vector<vector<int>> graph(v);
        for(auto e : edges){
            int u = e[0], v = e[1];
            
            graph[u].push_back(v);
            graph[v].push_back(u);
        }
        
        vector<int> col(v,-1);
        
        return solve(0,col,graph,v,m);
    }
};
```

Return -> [[Based on BFS-DFS Traversals]]

