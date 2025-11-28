https://www.geeksforgeeks.org/problems/minimum-sum-partition3317/1

Function -> abs(min(S1-S2)) where S1 and S2 are subsequence's of the array. Elements are not overlapping and partition is taken to whole of array.

S1 + S2 = Total sum
Therefore updated function -> abs(min(total sum - S2 - S2)) -> abs(min(total sum - 2 * S2))
where S2 is any subsequence.

`Goal -> Reach S2 closer to (total sum)/2` Boolean table for reaching any subsequence reaching target value. At 'n-1' row of DP table, we have traversed every possible subsequence combination. Now wherever the 'true' is present, we can take answer.

```
class Solution {
  public:
    int minDifference(vector<int>& arr){
        int n = arr.size();
        int total_sum = accumulate(arr.begin(),arr.end(),0);
        int target = total_sum/2;
        
        vector<vector<bool>> dp(n,vector<bool>(target+1,false));
        
        for(int i=0;i<n;i++) dp[i][0] = true;
        if(arr[0] <= target) dp[0][arr[0]] = true;
        
        for(int i=1; i<n; i++){
            for(int j=1; j <= target; j++){
                dp[i][j] = (j >= arr[i]) ? dp[i-1][j-arr[i]] : false;
                dp[i][j] = dp[i][j] || dp[i-1][j];
            }
        }
        
        int ans = INT_MAX;
        for(int j=0; j <= target; j++){
            if(dp[n-1][j])
                ans = min(ans,abs(total_sum-2*j));
        }
        
        return ans;
    }
};
```

Return -> [[DP on Subsequences]]

