https://leetcode.com/problems/number-of-longest-increasing-subsequence/

```
class Solution {
public:
    int findNumberOfLIS(vector<int>& nums) {
        int n = nums.size();
        vector<int> dp(n,1);
        vector<int> record(n,1);
        int maxi = 1;
  
        for(int i=1;i<n;i++){
            for(int j=0;j<i;j++){
                if(nums[j] < nums[i]){
                    if(dp[i] < 1+dp[j]) record[i] = record[j];
                    else if(dp[i] == 1+dp[j]) record[i] += record[j];

                    dp[i] = max(dp[i],1+dp[j]);
                }
            }
            if(maxi < dp[i]) maxi = dp[i];
        }
        
        int ans = 0;
        for(int i=0;i<n;i++){
            if(dp[i] == maxi)
                ans += record[i];
        }

        return ans;
    }
};
```

Return -> [[DP on LIS]]