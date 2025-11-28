https://leetcode.com/problems/path-with-maximum-probability/?envType=problem-list-v2&envId=shortest-path

```
class Solution {
public:
    double maxProbability(int n, vector<vector<int>>& edges, vector<double>& succProb, int start_node, int end_node) {
        vector<vector<pair<int,double>>> graph(n);
        for(int i=0;i<edges.size();i++){
            int u = edges[i][0];
            int v = edges[i][1];
            double w = succProb[i];
  
            graph[u].push_back({v,w});
            graph[v].push_back({u,w});
        }
  
        vector<double> maxProb(n,0.0);
        priority_queue<pair<double,int>> pq;
  
        maxProb[start_node] = 1.0;
        pq.push({1, start_node});

        while(!pq.empty()){
            auto [prob, node] = pq.top();
            pq.pop();
  
            if(node == end_node) return prob;

            for(auto [neigh, edgeProb] : graph[node]){
                if(prob * edgeProb > maxProb[neigh]){
                    maxProb[neigh] = prob * edgeProb;
                    pq.push({prob * edgeProb, neigh});
                }
            }
        }
        return maxProb[end_node];
    }
};
```

Return -> [[Shortest Path Algorithms]]

