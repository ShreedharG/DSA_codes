https://www.geeksforgeeks.org/problems/number-of-ways-to-arrive-at-destination/1

```
class Solution {
public:
    int countPaths(int n, vector<vector<int>>& roads){
        int mod = 1e9+7;
        vector<int> ways(n,0);
        vector<long long> t_time(n,LLONG_MAX);
  
        vector<vector<pair<int,int>>> graph(n);
        for(auto road : roads){
            int u = road[0], v = road[1], w = road[2];
            graph[u].push_back({v,w});
            graph[v].push_back({u,w});
        }
  
        priority_queue<
            pair<long long,int>,
            vector<pair<long long,int>>,
            greater<pair<long long,int>>
        > pq;
  
        pq.push({0,0});
        ways[0] = 1;
        t_time[0] = 0;
        
        while(!pq.empty()){
            auto [node_time,node] = pq.top();
            pq.pop();
  
            for(auto [n_node,time_btw] : graph[node]){
                long long newTime = node_time + time_btw;
                if(t_time[n_node] > newTime){
                    ways[n_node] = ways[node];
                    t_time[n_node] = newTime;
                    pq.push({newTime, n_node});
                }
                else if(t_time[n_node] == newTime)
                    ways[n_node] = (ways[n_node] + ways[node])%mod;
            }
        }
        return ways[n-1];
    }
};
```

Return -> [[Shortest Path Algorithms]]

