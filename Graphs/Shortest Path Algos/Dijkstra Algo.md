https://www.geeksforgeeks.org/problems/implementing-dijkstra-set-1-adjacency-matrix/1
###### Using Priority Queue
```
class Solution {
  public:
    vector<int> dijkstra(int V, vector<vector<int>> &edges, int src){
        vector<vector<pair<int,int>>> graph(V);        
        for(auto& edge : edges){
	        int u = edge[0], v = edge[1], w = edge[2];
            graph[u].push_back({v,w});
            graph[v].push_back({u,w});
        }
        
        vector<int> dis(V,INT_MAX);
        priority_queue<
	        pair<int,int>, 
	        vector<pair<int,int>>, 
	        greater<pair<int,int>>
	    > q;
	    
        q.push({0,src});
        dis[src] = 0;
        
        while(!q.empty()){
	        auto [dist, node] = q.top();
            q.pop();
            
            for(auto [neigh,edge_w] : graph[node]){                
                if(dis[neigh] > dist + edge_w){
                    dis[neigh] = dist + edge_w;
                    q.push({dist + edge_w,neigh});
                }
            }
        }
        return dis;
    }
};
```

Return -> [[Shortest Path Algorithms]]

