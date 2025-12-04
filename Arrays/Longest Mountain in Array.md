https://leetcode.com/problems/longest-mountain-in-array/?envType=problem-list-v2&envId=two-pointers

```
class Solution {
public:
    int longestMountain(vector<int>& arr) {
        int n = arr.size();
  
        vector<int> lis(n,1);
        for(int i=1;i<n;i++){
            if(arr[i-1] < arr[i])
                lis[i] = 1 + lis[i-1];
        }
  
        vector<int> lds(n,1);
        for(int i=n-2;i>=0;i--){
            if(arr[i] > arr[i+1])
                lds[i] = 1 + lds[i+1];
        }
  
        int ans = 0;
        for(int i=0;i<n;i++){
            if(lis[i]>1 && lds[i]>1)
                ans = max(ans, lis[i]+lds[i]-1);
        }
  
        return ans;
    }
};
```

Return -> [[Arrays, Prefix-Suffix, Hashing, Maps]]

