https://leetcode.com/problems/house-robber/
###### Recursive Stack
```
class Solution {
public:
    int solve(vector<int>& nums,int index){
        if(index==0) return nums[0];
        if(index<0) return 0;  

        int pick = nums[index] + solve(nums,index-2);
        int not_pick = 0 + solve(nums,index-1); 

        return max(pick,not_pick);
    }

    int rob(vector<int>& nums) {
        int n = nums.size();
        return solve(nums,n-1);
    }
};
```
###### Top-down Memoization
```
class Solution {
public:
    int solve(vector<int>& nums,int index,vector<int>& dp){
        if(index==0) return nums[0];
        if(index<0) return 0;  

        if(dp[index]!=-1) return dp[index]; 

        int pick = nums[index] + solve(nums,index-2,dp);
        int not_pick = 0 + solve(nums,index-1,dp);  

        return dp[index] = max(pick,not_pick);
    }

    int rob(vector<int>& nums) {
        int n = nums.size();
        vector<int> dp(n,-1);

        return solve(nums,n-1,dp);
    }
};
```
###### Space-optimised solution
```
class Solution {
public:
    int rob(vector<int>& nums) {
        int n = nums.size();
        int prev2 = 0;
        int prev1 = nums[0];
        int curri;  

        for(int i=1;i<n;i++){
            int take = nums[i];
            if(i>1)
                take += prev2;
            int not_take = 0 + prev1; 

            curri = max(take,not_take);
            prev2 = prev1;
            prev1 = curri;
        }
        return prev1;        
    }
};
```

Return -> [[DP 1D]]