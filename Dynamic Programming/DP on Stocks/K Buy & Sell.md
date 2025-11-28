https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/submissions/
###### Recursive
```
class Solution {
public:
    int max_p(int id,int canBuy,int cap,int n,vector<int>& prices){
        if(cap==0 || id==n) return 0;

        int profit = 0;
        if(canBuy)
            profit = max(-prices[id] + max_p(id+1,0,cap,n,prices),
                         max_p(id+1,1,cap,n,prices));
        else
            profit = max(prices[id] + max_p(id+1,1,cap-1,n,prices),
                         max_p(id+1,0,cap,n,prices));

        return profit;
    }
    int maxProfit(int k, vector<int>& prices){
        int n = prices.size();
        return max_p(0,1,k,n,prices);
    }
};
```
###### Memoization
```
class Solution {
public:
    int max_p(int id,int canBuy,int cap,vector<int>& prices,vector<vector<vector<int>>>& dp){
        if(cap==0 || id==prices.size()) return 0;
        if(dp[id][cap][canBuy]!=-1e7) return dp[id][cap][canBuy];

        int profit = 0;
        if(canBuy)
            profit = max(-prices[id] + max_p(id+1,0,cap,prices,dp),
                         max_p(id+1,1,cap,prices,dp));
        else
            profit = max(prices[id] + max_p(id+1,1,cap-1,prices,dp),
                         max_p(id+1,0,cap,prices,dp));

        return dp[id][cap][canBuy] = profit;
    }

    int maxProfit(int k, vector<int>& prices){
        int n = prices.size();
        vector<vector<vector<int>>> dp(n,vector<vector<int>>(k+1,vector<int>(2,-1e7)));
        return max_p(0,1,k,prices,dp);
    }
};
```
###### Tabulation
```
class Solution {
public:
    int maxProfit(int k,vector<int>& prices) {
        int n = prices.size();
        vector<vector<vector<int>>> dp(n+1,vector<vector<int>>(k+1,vector<int>(2,0)));

        for(int i=n-1;i>=0;i--){
            for(int j=k;j>=0;j--){
                for(int cB=1;cB>=0;cB--){
                    if(j==0){
                        dp[i][j][cB] = dp[i+1][j][cB];
                        break;
                    }
                    if(cB==1)
                        dp[i][j][cB] = max(-prices[i]+dp[i+1][j][0],
                                           dp[i+1][j][1]);
                    else
                        dp[i][j][cB] = max(+prices[i]+dp[i+1][j-1][1],
                                           dp[i+1][j][0]);
                }
            }
        }

        return dp[0][k][1];
    }
};
```

Return -> [[DP on Stocks]]