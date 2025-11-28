https://leetcode.com/problems/network-delay-time/

```
class Solution {
public:
    int networkDelayTime(vector<vector<int>>& times, int n, int k) {
        vector<vector<pair<int,int>>> graph(n+1);
        for(auto time : times)
            graph[time[0]].push_back({time[1],time[2]});
  
        priority_queue<
            pair<int,int>,
            vector<pair<int,int>>,
            greater<pair<int,int>>
        > pq;
        vector<int> time_taken(n+1,INT_MAX);
  
        pq.push({0,k});
        time_taken[k] = 0;
  
        while(!pq.empty()){
            auto [node_time,node] = pq.top();
            pq.pop();
  
            if(node_time > time_taken[node]) continue;
  
            for(auto [n_node,time_btw] : graph[node]){
                if(time_taken[n_node] > node_time+time_btw){
                    time_taken[n_node] = node_time+time_btw;
                    pq.push({node_time+time_btw,n_node});
                }
            }
        }

        int ans = 0;
        for(int i=1;i<=n;i++){
            if(time_taken[i] == INT_MAX)
                return -1;
            ans = max(ans,time_taken[i]);
        }
        return ans;
    }
};
```

Return -> [[Shortest Path Algorithms]]

