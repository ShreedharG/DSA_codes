https://leetcode.com/problems/cheapest-flights-within-k-stops/

```
class Solution {
public:
    int findCheapestPrice(int n, vector<vector<int>>& flights, int src, int dst, int k) {
	    if(src == dst) return 0;
        vector<vector<pair<int,int>>> graph(n);
        for(auto flight : flights)
            graph[flight[0]].push_back({flight[1],flight[2]});

        vector<int> minCost(n,INT_MAX);
        queue<vector<int>> q;

        q.push({0,src,0});
        minCost[src] = 0;
  
        while(!q.empty()){
            auto curr = q.front();
            q.pop();
  
            int stops = curr[0];
            int node = curr[1];
            int cost = curr[2];

            if(stops > k) continue;
            
            for(auto [airport,flight_cost] : graph[node]){
                if(stops <= k && minCost[airport] > cost + flight_cost){
                    minCost[airport] = cost + flight_cost;
                    q.push({stops+1, airport, cost + flight_cost});
                }
            }
        }
  
        return minCost[dst] == INT_MAX ? -1 : minCost[dst];
    }
};
```

Return -> [[Shortest Path Algorithms]]

