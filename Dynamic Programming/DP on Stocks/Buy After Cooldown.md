https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/ 
###### Recursive
```
class Solution {
public:
    int max_p(int id,int canBuy,int n,vector<int>& prices){
        if(id>=n) return 0;
        int profit = 0;

        if(canBuy)
            profit = max(-prices[id] + max_p(id+1,0,n,prices),
                         max_p(id+1,1,n,prices));
        else
            profit = max(prices[id] + max_p(id+2,1,n,prices),
                         max_p(id+1,0,n,prices));

        return profit;
    }

    int maxProfit(vector<int>& prices){
        int n = prices.size();
        return max_p(0,1,n,prices);        
    }
};
```
###### Memoization
```
class Solution {
public:
    int max_p(int id,int canBuy,int n,vector<int>& prices,vector<vector<int>>& dp){
        if(id>=n) return 0;
        if(dp[id][canBuy]!=-1e7) return dp[id][canBuy];

        int profit = 0;
        if(canBuy)
            profit = max(-prices[id] + max_p(id+1,0,n,prices,dp),
                         max_p(id+1,1,n,prices,dp));

        else
            profit = max(prices[id] + max_p(id+2,1,n,prices,dp),
                         max_p(id+1,0,n,prices,dp));

        return dp[id][canBuy] = profit;
    }

    int maxProfit(vector<int>& prices){
        int n = prices.size();
        vector<vector<int>> dp(n,vector<int>(2,-1e7));

        return max_p(0,1,n,prices,dp);        
    }
};
```
###### Tabulation
```
class Solution {
public:
    int maxProfit(vector<int>& prices){
        int n = prices.size();
        vector<vector<int>> dp(n+2,vector<int>(2,0));

        for(int i=n-1;i>=0;i--){
            for(int j=1;j>=0;j--){
                if(j==1)
                    dp[i][j] = max(-prices[i]+dp[i+1][0],dp[i+1][1]);
                else
                    dp[i][j] = max(+prices[i]+dp[i+2][1],dp[i+1][0]);
            }
        }
        return dp[0][1];        
    }
};
```

Return -> [[DP on Stocks]]
