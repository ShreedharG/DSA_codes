https://www.geeksforgeeks.org/problems/minimum-multiplications-to-reach-end/1

```
class Solution {
  public:
    int minimumMultiplications(vector<int>& arr, int start, int end){
        if(start==end) return 0;
        
        vector<int> steps(1e5,INT_MAX);
        queue<pair<int,int>> q;
        int mod = 1e5;
        
        steps[start] = 0;
        q.push({0,start});
        
        while(!q.empty()){
            auto [steps_curr,node] = q.front();
            q.pop();
            
            for(int k=0;k<arr.size();k++){
                int val = (node*arr[k])%mod;
                
                if(val == end) return steps[node]+1;
                
                if(steps[val] > steps[node]+1){
                    q.push({steps[node]+1,val});
                    steps[val] = steps[node]+1;
                }
            }
        }
        return -1;
    }
};
```

Return -> [[Shortest Path Algorithms]]

