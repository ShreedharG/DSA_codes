https://leetcode.com/problems/partition-equal-subset-sum/

###### Recursion (2^N time complexity)
```
class Solution {
public:
    bool solve(int index,vector<int>& nums,int target){
        if(target==0) return true;
        if(index<0) return false;
        
        bool take = false;
		if(nums[index] <= target)
            take = solve(index-1,nums,target-nums[index]);          
        bool not_take = solve(index-1,nums,target);

        return (take||not_take);
    }

    bool canPartition(vector<int>& nums) {
        int n = nums.size();
        int sum = 0;
        for(int i=0;i<n;i++)
            sum += nums[i];

        if(sum%2==1) return false;
        int target = sum/2;

        return solve(n-1,nums,target);        
    }
};
```

###### Tabulation Approach
```
class Solution {
public:
    bool canPartition(vector<int>& nums) {
        int n = nums.size();
        int sum = 0;
        for(int i=0;i<n;i++)
            sum += nums[i];
            
        if(sum%2==1) return false; 
        int target = sum/2;

        vector<vector<bool>> dp(n+1,vector<bool>(target+1,false));

        for(int i=0;i<=n;i++)
            dp[i][0] = true;

        for(int i=1;i<=n;i++){
            for(int j=1;j<=target;j++){
                bool not_take = dp[i-1][j];
                bool take = false;
                if(nums[i-1] <= j)
                    take = dp[i-1][j-nums[i-1]];
                dp[i][j] = take || not_take;
            }
        }
        return dp[n][target];
    }
};
```

Return -> [[DP on Subsequences]]