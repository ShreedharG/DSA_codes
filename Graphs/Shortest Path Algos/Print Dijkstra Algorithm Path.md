https://www.geeksforgeeks.org/problems/shortest-path-in-weighted-undirected-graph/1

```
class Solution {
  public:
    vector<int> shortestPath(int n, int m, vector<vector<int>>& edges){
        if(m==0) return {-1};
        
        vector<vector<pair<int,int>>> graph(n+1);
        for(auto& edge : edges){
            int u = edge[0];
            int v = edge[1];
            int w = edge[2];
            
            graph[u].push_back({v,w});
            graph[v].push_back({u,w});
        }
        
        priority_queue<pair<int,int>,vector<pair<int,int>>,
				       greater<pair<int,int>>> q;
        vector<int> dis(n+1,INT_MAX);
        
        vector<int> parent(n+1);
        for(int i=1;i<=n;i++)
            parent[i] = i;
        
        q.push({0,1});
        dis[1] = 0;
        
        while(!q.empty()){
            auto [dist,node] = q.top();
            q.pop();
            
            for(auto neigh : graph[node]){
                int adjNode = neigh.first;
                int edge_w = neigh.second;
                
                if(dis[adjNode] > dist + edge_w){
                    dis[adjNode] = dist + edge_w;
                    parent[adjNode] = node;
                    q.push({dist + edge_w,adjNode});
                }
            }
        }
        
        if(dis[n] == INT_MAX) return {-1};
        
        vector<int> path;
        int curr = n;
        while(parent[curr] != curr){
            path.push_back(curr);
            curr = parent[curr];
        }
        
        path.push_back(1);
        path.push_back(dis[n]);
        
        reverse(path.begin(),path.end());
        return path;
    }
};
```

Return -> [[Shortest Path Algorithms]]

