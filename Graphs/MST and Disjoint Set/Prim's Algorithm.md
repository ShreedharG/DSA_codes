https://www.geeksforgeeks.org/problems/minimum-spanning-tree/1

```
class Solution {
  public:
    int spanningTree(int V, vector<vector<int>>& edges){
        vector<bool> vis(V,false);
        vector<vector<pair<int,int>>> graph(V);
        for(auto edge : edges){
            graph[edge[0]].push_back({edge[1],edge[2]});
            graph[edge[1]].push_back({edge[0],edge[2]});
        }
        priority_queue<
            pair<int,int>,
            vector<pair<int,int>>,
            greater<pair<int,int>>
        > pq;
        int sum = 0;
        
        pq.push({0,0});        
        while(!pq.empty()){
            auto [weight, node] = pq.top();
            pq.pop();
            
            if(!vis[node]){
                vis[node] = true;
                sum += weight;
            }
            for(auto [n_node,edgeW] : graph[node]){
                if(!vis[n_node])
                    pq.push({edgeW,n_node});
            }
        }        
        return sum;
    }
};
```

Return -> [[MST and Disjoint Set Problems]]

