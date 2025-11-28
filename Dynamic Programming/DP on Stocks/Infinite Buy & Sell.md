https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/
###### Recursive
```
class Solution {
public:
    int max_f(int index,int canBuy,vector<int>& prices,int n){
        if(index==n) return 0;

        int profit = 0;
        if(canBuy)
            profit = max(-prices[index] + max_f(index+1,0,prices,n),
                         0 + max_f(index+1,1,prices,n));

        else
            profit = max(prices[index] + max_f(index+1,1,prices,n),
                         max_f(index+1,0,prices,n));
        return profit;
    }

    int maxProfit(vector<int>& prices) {
        int n = prices.size();        
        return max_f(0,1,prices,n);        
    }
};
```
###### Memoization
```
class Solution {
public:
    int max_f(int index,int canBuy,vector<int>& prices,int n,vector<vector<int>>& dp){
        if(index==n) return 0;
        if(dp[index][canBuy]!=-1) return dp[index][canBuy];
        int profit = 0;

        if(canBuy)
            profit = max(-prices[index] + max_f(index+1,0,prices,n,dp),
                         0 + max_f(index+1,1,prices,n,dp));

        else
            profit = max(prices[index] + max_f(index+1,1,prices,n,dp),
                         max_f(index+1,0,prices,n,dp));

        return dp[index][canBuy] = profit;
    }

    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        vector<vector<int>> dp(n,vector<int>(2,-1));

        return max_f(0,1,prices,n,dp);        
    }
};
```
###### Tabulation
```
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        vector<vector<int>> dp(n+1,vector<int>(2,0));
  
        for(int i=n-1;i>=0;i--){
            for(int j=1;j>=0;j--){
                if(j==1)
                    dp[i][1] = max(-prices[i]+dp[i+1][0],dp[i+1][1]);
                else
                    dp[i][j] = max(+prices[i]+dp[i+1][1],dp[i+1][0]);
            }
        }
        return dp[0][1];        
    }
};
```

Return -> [[DP on Stocks]]