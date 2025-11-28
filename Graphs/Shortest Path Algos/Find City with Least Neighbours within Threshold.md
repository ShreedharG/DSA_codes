https://leetcode.com/problems/find-the-city-with-the-smallest-number-of-neighbors-at-a-threshold-distance/

```
class Solution {
public:
    int findTheCity(int n,vector<vector<int>>& edges, int distanceThreshold) {
        vector<vector<int>> g(n,vector<int>(n,INT_MAX));
        for(auto edge : edges){
            int u = edge[0], v = edge[1], w = edge[2];
            g[u][v] = w;
            g[v][u] = w;
        }
  
        for(int i=0; i<n; i++) graph[i][i] = 0;
  
        for(int via=0; via < n; via++){
            for(int i=0;i<n;i++){
                for(int j=0;j<n;j++){
                    if(g[i][via]==INT_MAX || g[via][j]==INT_MAX)
                        continue;
                    g[i][j] = min(g[i][j], g[i][via]+g[via][j]);
                }
            }
        }

        int min_num_cities = n;
        int city = -1;
  
        for(int i=0;i<n;i++){
            // check for individual city[i] now
            int cities = 0;
            for(int j=0;j<n;j++){
                if(j != i && g[i][j] <= distanceThreshold)
	                cities++;
            }
            if(min_num_cities >= cities){
                min_num_cities = cities;
                city = i;
            }
        }
  
        // Return the city NOT the number of cities within threshold
        return city;
    }
};
```

Return -> [[Shortest Path Algorithms]]


