https://www.geeksforgeeks.org/problems/max-sum-subarray-of-size-k5313/1

```
class Solution {
  public:
    int maxSubarraySum(vector<int>& arr, int k) {
        int n = arr.size();
        int sum = 0;
        int ans;
        
        for(int i=0;i<k;i++) sum += arr[i];  
        
        ans = sum;
        for(int i=k;i<n;i++){
            sum += arr[i] - arr[i-k];
            ans = max(ans,sum);
        }
        return ans;
    }
};
```

Return -> [[Sliding Window, 2 Pointer Approach]]

