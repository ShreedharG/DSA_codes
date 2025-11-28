https://leetcode.com/problems/largest-divisible-subset/

```
class Solution {
public:
    vector<int> largestDivisibleSubset(vector<int>& nums) {
        int n = nums.size();
        sort(nums.begin(),nums.end());

        vector<int> dp(n,1);
        vector<int> hash_arr(n);
        for(int i=0;i<n;i++)
            hash_arr[i] = i;

        int last_id = 0;
        int maxi = 1;

        for(int i=0;i<n;i++){
            for(int j=0;j<i;j++){
                if((nums[i]%nums[j]==0) && (dp[i]<1+dp[j])){
                    dp[i] = 1+dp[j];
                    hash_arr[i] = j;
                }
            }

            if(maxi < dp[i]){
                maxi = dp[i];
                last_id = i;
            }
        }
  
        vector<int> ans;
        ans.push_back(nums[last_id]);
        while(hash_arr[last_id]!=last_id){
            last_id = hash_arr[last_id];
            ans.push_back(nums[last_id]);
        }
        reverse(ans.begin(),ans.end());
        
        return ans;
    }
};
```

Return -> [[DP on LIS]]