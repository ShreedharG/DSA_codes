https://www.geeksforgeeks.org/problems/snake-and-ladder-problem4816/1

```
class Solution {
  public:
    int minThrow(int N, int arr[]){
        vector<int> vis(31,-1);
        queue<pair<int,int>> q;
        map<int,int> myMap;
        for(int j=0;j<2*N;j+=2)
            myMap[arr[j]] = arr[j+1];
        
        vis[1] = 0;
        q.push({1,0});
        
        while(!q.empty()){
            int pos = q.front().first;
            int steps = q.front().second;
            q.pop();
            
            if(pos == 30) return steps;
            
            for(int i=1;i<=6;i++){
                int new_pos = pos+i;
                
                if(myMap.find(new_pos) != myMap.end())
                    new_pos = myMap[new_pos];
                
                if(vis[new_pos] == -1){
                    q.push({new_pos,steps+1});
                    vis[new_pos] = steps+1;
                }
            }
        }
        return -1;
        
    }
};
```

Return -> [[Based on BFS-DFS Traversals]]

