https://leetcode.com/problems/longest-increasing-subsequence/
###### Recursive
```
class Solution {
public:
    int find_length(int id,int prev_id,vector<int>& nums,int n,vector<vector<int>>& dp){
        if(id==n) return 0;
        if(dp[id][prev_id+1]!=-1) return dp[id][prev_id+1];
        
        int take = 0;
        if(prev_id==-1 || nums[id]>nums[prev_id])
            take = 1+find_length(id+1,id,nums,n,dp);

        int not_take = find_length(id+1,prev_id,nums,n,dp);
        
        return dp[id][prev_id+1] = max(take,not_take);
    }

    int lengthOfLIS(vector<int>& nums) {
        int n = nums.size();
        vector<vector<int>> dp(n,vector<int>(n+1,-1));
  
        return find_length(0,-1,nums,n,dp);
    }
};
```

###### Memoization
```
class Solution {
public:
    int find_length(int id,int prev_id,vector<int>& nums,int n,vector<vector<int>>& dp){
        if(id==n) return 0;
        if(dp[id][prev_id+1]!=-1) return dp[id][prev_id+1];

        int take = 0;
        if(prev_id==-1 || nums[id]>nums[prev_id])
            take = 1+find_length(id+1,id,nums,n,dp);
            
        int not_take = find_length(id+1,prev_id,nums,n,dp);

        return dp[id][prev_id+1] = max(take,not_take);
    }

    int lengthOfLIS(vector<int>& nums) {
        int n = nums.size();
        vector<vector<int>> dp(n,vector<int>(n+1,-1));
  
        return find_length(0,-1,nums,n,dp);
    }
};
```
###### Tabulation
```
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        int n = nums.size();
        vector<vector<int>> dp(n+1,vector<int>(n+1,0));

        for (int i = n-1; i>=0; i--) {
            for (int prev = i-1; prev>=-1; prev--) {
                int notTake = dp[i+1][prev+1];
                
                int take = 0;
                if (prev == -1 || nums[i] > nums[prev])
                    take = 1 + dp[i+1][i+1];
                    
                dp[i][prev+1] = max(take, notTake);
            }
        }
        return dp[0][0];
    }
};
```

Return -> [[DP on LIS]]