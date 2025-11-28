https://www.geeksforgeeks.org/problems/shortest-path-in-undirected-graph-having-unit-distance/1

```
class Solution {
  public:
    vector<int> shortestPath(vector<vector<int>>& adj, int src){
        int n = adj.size();
        vector<int> minDis(n,INT_MAX);
        queue<int> q;
        
        minDis[src] = 0;
        q.push(src);        
        while(!q.empty()){
            int node = q.front();
            q.pop();
            
            for(auto neigh : adj[node]){
                if(minDis[neigh] > 1+minDis[node]){
                    minDis[neigh] = minDis[node]+1;
                    q.push(neigh);
                }
            }
        }
        
        for(int i=0;i<n;i++)
            minDis[i] = (minDis[i] == INT_MAX) ? -1 : minDis[i];
        
        return minDis;
    }
};
```

Return -> [[Shortest Path Algorithms]]

