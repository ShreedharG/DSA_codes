https://leetcode.com/problems/coin-change/
###### Top-down Memoization
```
class Solution {
public:
    int min_ways(int index,vector<int>& coins,int amount,vector<vector<int>>& dp){
        if(index==0){
            if(amount%coins[index] == 0)
                return dp[index][amount] = amount/coins[index];
            else
                return 1e9;
        }

        if(dp[index][amount]!=-1)
            return dp[index][amount];  

        int not_take = min_ways(index-1,coins,amount,dp);
        int take = 1e9;
        if(amount >= coins[index])
            take = 1 + min_ways(index,coins,amount-coins[index],dp);
        return dp[index][amount] = min(take,not_take);
    }

    int coinChange(vector<int>& coins, int amount) {
        int n = coins.size();
        vector<vector<int>> dp(n,vector<int>(amount+1,-1));
        sort(coins.begin(),coins.end());

        int result = min_ways(n - 1, coins, amount, dp);
        return (result >= 1e9) ? -1 : result;
    }
};
```

###### Tabulation
```
class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {
        int n = coins.size();
        vector<vector<int>> dp(n,vector<int>(amount+1,1e9));
  
        for(int j=0;j<=amount;j++){
            if(j%coins[0]==0)
                dp[0][j] = j/coins[0];
        }

        for(int i=1;i<n;i++){
            for(int j=0;j<=amount;j++){
                int not_take = dp[i-1][j];
                int take = (coins[i] <= j) ? 1 + dp[i][j-coins[i]] : 1e9;

                dp[i][j] = min(not_take,take);
            }
        }
        return ((dp[n-1][amount]>=1e9) ? -1 : dp[n-1][amount]);
    }
};
```

Return -> [[DP on Subsequences]]


