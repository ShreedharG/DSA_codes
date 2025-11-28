https://www.geeksforgeeks.org/problems/subset-sum-problem-1611555638/1
###### Tabulation
```
class Solution {
  public:
    bool isSubsetSum(vector<int>& arr, int sum) {
        int n = arr.size();
        vector<vector<bool>> dp(n,vector<bool>(sum+1,false));
        
        for(int i=0;i<n;i++)
            dp[i][0] = true;
        
        if(arr[0] <= sum)
            dp[0][arr[0]] = true;
        
        for(int i=1;i<n;i++){
            for(int j=1;j<=sum;j++){
                bool not_take = dp[i-1][j];
                bool take = (arr[i] <= j) ? dp[i-1][j-arr[i]] : false;
                
                dp[i][j] = take || not_take;
            }
        }
        
        return dp[n-1][sum];   
    }
};
```

Return -> [[DP on Subsequences]]
