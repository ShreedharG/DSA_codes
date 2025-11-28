https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/

###### Recursive
```
class Solution {
public:
    int max_profit_2trans(int i,int canBuy,int cap,int n,vector<int>& prices){
        if(cap==0 || i==n) return 0;

        int profit = 0;
        if(canBuy)
            profit = max(-prices[i]+max_profit_2trans(i+1,0,cap,n,prices),
                      max_profit_2trans(i+1,1,cap,n,prices));

        else
            profit = max(prices[i]+max_profit_2trans(i+1,1,cap-1,n,prices),
                      max_profit_2trans(i+1,0,cap,n,prices));

        return profit;
    }

    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        return max_profit_2trans(0,1,2,n,prices);
    }
};
```

###### Memoization
```
class Solution {
public:
    int max_p(int id,int cap,int canBuy,int n,vector<int>& prices,vector<vector<vector<int>>>& dp){
        if(cap==0 || index==n) return 0;
        if(dp[id][cap][canBuy]!=-1e7) return dp[id][cap][canBuy];

        int profit = 0;
        if(canBuy)
            profit = max(-prices[id] + max_p(id+1,cap,0,n,prices,dp),
                      max_p(id+1,cap,1,n,prices,dp));
        else
            profit = max(prices[id] + max_p(id+1,cap-1,1,n,prices,dp),
                      max_p(id+1,cap,0,n,prices,dp));

        return dp[id][cap][canBuy] = profit;
    }
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        vector<vector<vector<int>>> dp(n,vector<vector<int>>(3,vector<int>(2,-1e7)));
        
        return max_p(0,2,1,n,prices,dp);
    }
};
```

###### Tabulation
```
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        vector<vector<vector<int>>> dp(n+1,vector<vector<int>>(3,vector<int>(2,0)));
        for(int i=n-1;i>=0;i--){
            for(int j=2;j>=0;j--){
                for(int k=1;k>=0;k--){
                    if(j==0){
                        dp[i][j][k] = dp[i+1][j][k];
                        break;
                    }
                    if(k==1)
                        dp[i][j][k] = max(-prices[i]+dp[i+1][j][0],
					                       dp[i+1][j][1]);
                    else
                        dp[i][j][k] = max(+prices[i]+dp[i+1][j-1][1],
					                       dp[i+1][j][0]);
                }
            }
        }
        return dp[0][2][1];
    }
};
```

Return -> [[DP on Stocks]]