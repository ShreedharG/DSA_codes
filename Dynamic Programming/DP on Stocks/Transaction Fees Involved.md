https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/
###### Recursive
```
class Solution {
public:
    int fees;
    int n;

    int max_p_transfee(int id,int canBuy,vector<int>& prices){
        if(id==n) return 0;
        int profit = 0;
        
        if(canBuy)
            profit = max(-prices[id] + max_p_transfee(id+1,0,prices),
                         max_p_transfee(id+1,1,prices));
        else
            profit = max(prices[id] - fees + max_p_transfee(id+1,1,prices),
                         max_p_transfee(id+1,0,prices));
        
        return profit;
    }

    int maxProfit(vector<int>& prices, int fee){
        n = prices.size();
        fees = fee;
        return max_p_transfee(0,1,prices);        
    }
};
```
###### Memoization
```
class Solution {
public:
    int fees;
    int n;
    int max_p(int id,int canBuy,vector<int>& prices,vector<vector<int>>& dp){
        if(id==n) return 0;
        if(dp[id][canBuy]!=-1e7) return dp[id][canBuy];

        int profit = 0;
        if(canBuy)
            profit = max(-prices[id] + max_p(id+1,0,prices,dp),
                         max_p(id+1,1,prices,dp));
        else
            profit = max(prices[id] - fees + max_p(id+1,1,prices,dp),
                         max_p(id+1,0,prices,dp));
        
        return dp[id][canBuy] = profit;
    }

    int maxProfit(vector<int>& prices, int fee){
        n = prices.size();
        fees = fee;
        vector<vector<int>> dp(n,vector<int>(2,-1e7));

        return max_p(0,1,prices,dp);        
    }
};
```
###### Bottom-up Tabulation
```
class Solution {
public:
    int maxProfit(vector<int>& prices, int fee) {
        int n = prices.size();
        vector<vector<int>> dp(n+1,vector<int>(2,0));

        for(int i=n-1;i>=0;i--){
            for(int j=1;j>=0;j--){
                if(j==1)
                    dp[i][j] = max(-prices[i]+dp[i+1][0],dp[i+1][j]);
                else
                    dp[i][j] = max(prices[i]-fee+dp[i+1][1],dp[i+1][j]);
            }
        }
        return dp[0][1];
    }
};
```

Return -> [[DP on Stocks]]
