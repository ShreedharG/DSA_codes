https://www.geeksforgeeks.org/problems/smallest-subarray-with-sum-greater-than-x5651/1

```
class Solution {
  public:
    int smallestSubWithSum(int x, vector<int>& arr){
        int n = arr.size();
        int left = 0;
        int sum = 0;
        int ans = INT_MAX;
        
        for(int right=0; right < n; right++){
            sum += arr[right];
            
            while(sum > x){
                ans = min(ans, right-left+1);
                sum -= arr[left];
                left++;
            }
        }
          
        return (ans == INT_MAX ? 0 : ans);
    }
};
```

Return -> [[Sliding Window, 2 Pointer Approach]]

