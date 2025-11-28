https://www.geeksforgeeks.org/problems/detect-cycle-in-a-directed-graph/1

```
class Solution {
  public:
    vector<vector<int>> adj_inD(int V,vector<vector<int>> &edges,vector<int>& inDegree){
        vector<vector<int>> graph(V);
        for(int i=0;i<edges.size();i++){
            graph[edges[i][0]].push_back(edges[i][1]);
            inDegree[edges[i][1]]++;
        }
        return graph;
    }
    
    bool isCyclic(int V, vector<vector<int>> &edges){
        vector<int> inDegree(V,0);
        vector<vector<int>> adj = adj_inD(V,edges,inDegree);
        vector<int> top_sort;
        
        queue<int> q;
        for(int i=0;i<V;i++){
            if(inDegree[i] == 0)
                q.push(i);
        }
        
        while(!q.empty()){
            int node = q.front();
            q.pop();
            
            top_sort.push_back(node);
            
            for(auto neigh : adj[node]){
                inDegree[neigh]--;
                if(inDegree[neigh] == 0)
                    q.push(neigh);
            }
        }
        
        return (top_sort.size() != V);
    }
};
```

Return -> [[Topological Sort Problems]]

