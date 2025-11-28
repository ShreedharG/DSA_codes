https://www.geeksforgeeks.org/problems/minimum-platforms-1587115620/1

```
class Solution {
  public:
    int findPlatform(vector<int>& arr, vector<int>& dep) {
        int n = arr.size();
        
        sort(arr.begin(),arr.end());
        sort(dep.begin(),dep.end());
        
        int platforms = 1;
        int required = 1;
        
        int i = 1;
        int j = 0;
        while(i<n && j<n){
            if(arr[i] <= dep[j]){
                platforms++;
                i++;
            }
            else{
                platforms--;
                j++;
            }
            required = max(required, platforms);
        }
        return required;
    }
};
```

Return -> [[Greedy Algorithms]]

