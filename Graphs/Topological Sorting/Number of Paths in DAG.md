https://www.geeksforgeeks.org/problems/possible-paths-between-2-vertices-1587115620/1

```
class Solution {
public:
    int countPaths(int V, vector<int> adj[], int source, int destination) {
        vector<int> indegree(V, 0);
        vector<int> paths(V, 0);
        
        for(int u=0; u<V; u++){
            for(int v : adj[u])
                indegree[v]++;
        }
        
        queue<int> q;
        for(int i=0;i<V;i++){
            if(indegree[i]==0) 
                q.push(i);
        }
        
        paths[source] = 1;
        while(!q.empty()){
            int u = q.front(); 
            q.pop();
            
            for(int v : adj[u]){
                paths[v] += paths[u];
                indegree[v]--;
                
                if(indegree[v]==0) 
                    q.push(v);
            }
        }
        return paths[destination];
    }
};
```

Return -> [[Topological Sort Problems]]

