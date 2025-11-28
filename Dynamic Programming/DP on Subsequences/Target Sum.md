https://leetcode.com/problems/target-sum/description/
###### Brute Force Backtrack
```
class Solution {
public:
    int find_ways(int id,int target,int n,vector<int>& nums){
        if(id==n) return (target==0 ? 1 : 0); 
         
        int pos = find_ways(id+1,target-nums[id],n,nums);
        int neg = find_ways(id+1,target+nums[id],n,nums);

        return (pos+neg);
    }

    int findTargetSumWays(vector<int>& nums, int target) {
        int n = nums.size();
        return find_ways(0,target,n,nums);
    }
};
```

###### Optimised
```
class Solution {
public:
    int findTargetSumWays(vector<int>& nums, int target) {
        int n = nums.size();
        int sum = accumulate(nums.begin(),nums.end(),0);

        if((sum+target)%2==1 || abs(target) > sum) return 0;

        int n_target = (sum+target)/2;
        vector<vector<int>> dp(n,vector<int>(n_target+1,0));
  
        if(nums[0]==0)
            dp[0][0] = 2;
        else{
            dp[0][0] = 1;
            if(nums[0] <= n_target)
                dp[0][nums[0]] = 1;
        }
  
        for(int i=1;i<n;i++){
            for(int j=0; j <= n_target; j++){
                if(nums[i]==0)
                    dp[i][j] = 2*dp[i-1][j];
                else{
                    dp[i][j] = j >= nums[i] ? dp[i-1][j-nums[i]] : 0;
                    dp[i][j] = dp[i][j] + dp[i-1][j];
                }
            }
        }
        return dp[n-1][n_target];
    }
};
```

Return -> [[DP on Subsequences]]

