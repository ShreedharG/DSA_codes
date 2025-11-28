https://www.geeksforgeeks.org/problems/path-with-minimum-effort/1

```
class Solution {
  public:
    bool Valid(int ni,int nj,int rows,int columns){
        return (ni>=0 && nj>=0 && ni<rows && nj<columns);
    }
    
    int MinimumEffort(int rows, int columns, vector<vector<int>> &heights){
        vector<int> dx = {-1,1,0,0};
        vector<int> dy = {0,0,-1,1};
        
        priority_queue<
            pair<int,pair<int,int>>,
            vector<pair<int,pair<int,int>>>,
            greater<pair<int,pair<int,int>>>
        > pq;
        vector<vector<int>> dis(rows, vector<int>(columns, INT_MAX));
        dis[0][0] = 0;
        
        pq.push({0,{0,0}});
        while(!pq.empty()){
            auto [effort, pos] = pq.top();
            pq.pop();
            int i = pos.first;
            int j = pos.second;
            
            if(i==rows-1 && j==columns-1) return effort;
            
            for(int k=0;k<4;k++){
                int ni = i + dx[k];
                int nj = j + dy[k];
                
                if(Valid(ni,nj,rows,columns)){
                    int newE = max(effort,abs(heights[i][j]-heights[ni][nj]));
                    if(newE < dis[ni][nj]){
                        dis[ni][nj] = newE;
                        pq.push({newE,{ni,nj}});
                    }
                }
            }
        }
        return -1;
    }
};
```

Return -> [[Shortest Path Algorithms]]

