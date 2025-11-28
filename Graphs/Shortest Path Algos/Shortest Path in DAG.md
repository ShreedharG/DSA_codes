https://www.geeksforgeeks.org/problems/shortest-path-in-undirected-graph/1

```
class Solution {
  public:
    vector<int> shortestPath(int V, int E, vector<vector<int>>& edges){
        vector<vector<pair<int,int>>> graph(V);
        vector<int> inDegree(V,0);
        vector<int> minPathSrc(V,INT_MAX);
        
        for(int i=0;i<E;i++){
            graph[edges[i][0]].push_back({edges[i][1],edges[i][2]});
            inDegree[edges[i][1]]++;
        }
        
        minPathSrc[0] = 0;        
        queue<int> q;
        for(int i=0;i<V;i++){
            if(inDegree[i] == 0)
                q.push(i);
        }
        
        while(!q.empty()){
            int node = q.front();
            q.pop();
            
            for(auto& neigh : graph[node]){
                int v = neigh.first;
                int w = neigh.second;
                
                inDegree[v]--;
                if(minPathSrc[node] != INT_MAX)
                    minPathSrc[v] = min(minPathSrc[v],minPathSrc[node]+w);
                
                if(inDegree[v]==0)
                    q.push(v);
            }
        }

        for(int i=0;i<V;i++)
            minPathSrc[i] = (minPathSrc[i] == INT_MAX) ? -1 : minPathSrc[i];
        
        return minPathSrc;
    }
};
```


Return -> [[Shortest Path Algorithms]]

