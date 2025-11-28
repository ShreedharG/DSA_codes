https://leetcode.com/problems/swim-in-rising-water/description/

```
class Solution {
public:
    bool inBoard(int ni,int nj,int n){
        return (ni>=0 && nj>=0 && ni<n && nj<n);
    }
  
    int swimInWater(vector<vector<int>>& grid) {
        int n = grid.size();
        int dx[] = {-1,1,0,0};
        int dy[] = {0,0,-1,1};
  
        vector<vector<int>> dis(n,vector<int>(n,INT_MAX));
        priority_queue<
            pair<int,pair<int,int>>,
            vector<pair<int,pair<int,int>>>,
            greater<pair<int,pair<int,int>>>
        > pq;

        dis[0][0] = grid[0][0];
        pq.push({grid[0][0],{0,0}});

        while(!pq.empty()){
            int time = pq.top().first;
            int i = pq.top().second.first;
            int j = pq.top().second.second;
            pq.pop();
  
            if(i==n-1 && j==n-1) return time;
  
            for(int k=0;k<4;k++){
                int ni = i + dx[k];
                int nj = j + dy[k];

                if(!inBoard(ni,nj,n)) continue;

                int newTime = max(time,grid[ni][nj]);
                if(dis[ni][nj] > newTime){
                    dis[ni][nj] = newTime;
                    pq.push({newTime,{ni,nj}});
                }
            }
        }
        return -1;
    }
};
```

Return -> [[Shortest Path Algorithms]]

