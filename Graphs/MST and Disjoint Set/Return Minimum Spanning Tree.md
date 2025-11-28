https://www.naukri.com/code360/problems/prim-s-mst_1095633?leftPanelTabValue=SUBMISSION

```
#include <bits/stdc++.h> 
vector<pair<pair<int, int>, int>> calculatePrimsMST(int n, int m, vector<pair<pair<int, int>, int>> &g){
    vector<pair<pair<int, int>, int>> ans;
    vector<vector<pair<int,int>>> graph(n+1);
  
    for(int i=0; i < g.size(); i++){
        int u = g[i].first.first;
        int v = g[i].first.second;
        int w = g[i].second;
        
        bool found = false;
        for(auto& pairs : graph[u]){
            if(pairs.first == v){
                found = true;
                pairs.second = min(w,pairs.second);
                break;
            }
        }
        if(!found) graph[u].push_back({v,w});

        found = false;
        for(auto& pairs : graph[v]){
            if(pairs.first == u){
                found = true;
                pairs.second = min(pairs.second,w);
                break;
            }
        }
        if(!found) graph[v].push_back({u,w});
    }

    vector<bool> vis(n+1,false);
    priority_queue<
        pair<int,pair<int,int>>,
        vector<pair<int,pair<int,int>>>,
        greater<pair<int,pair<int,int>>>
    > pq;
  
    pq.push({0,{1,-1}});
    while(!pq.empty()){
        auto [weight, nodes] = pq.top();
        int node = nodes.first;
        int parent = nodes.second;
        pq.pop();
  
        if(!vis[node]){
            vis[node] = true;
            if(parent != -1) ans.push_back({{node,parent},weight});
  
            for(auto [n_node,edgeW] : graph[node]){
                if(!vis[n_node])
                    pq.push({edgeW,{n_node,node}});
            }
        }
    }
    return ans;
}
```

Return -> [[MST and Disjoint Set Problems]]

