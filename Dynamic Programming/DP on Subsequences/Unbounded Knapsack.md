https://www.geeksforgeeks.org/problems/knapsack-with-duplicate-items4201/1
###### Tabulation
```
class Solution {
  public:
    int knapSack(vector<int>& val, vector<int>& wt, int capacity){
        int n = val.size();
        vector<vector<int>> dp(n,vector<int>(capacity+1,0));
        
        for(int i=wt[0];i<=capacity;i++)
            dp[0][i] = (i/wt[0])*val[0];
        
        for(int i=1;i<n;i++){
            for(int j=0;j<=capacity;j++){
                int not_take = dp[i-1][j];
                int take = (wt[i] <= j) ? val[i]+dp[i][j-wt[i]] : 0;
    
                dp[i][j] = max(take,not_take);
            }
        }
        return dp[n-1][capacity];
    }
};
```

Return -> [[DP on Subsequences]]
