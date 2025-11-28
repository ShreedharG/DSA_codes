https://leetcode.com/problems/coin-change-ii/
###### Tabulation
```
class Solution {
public:
    int change(int amount, vector<int>& coins){
        int n = coins.size();
        vector<vector<int>> dp(n,vector<int>(amount+1,0));

        bool even = true;
        for(int i=0;i<n;i++){
            if(coins[i]%2==1){
                even = false;
                break;
            }
        }
        if(amount%2==1 && even) return 0;

        for(int i=0;i<=amount;i++){
            if(i%coins[0]==0)
                dp[0][i] = 1;
        }
        
        for(int i=1;i<n;i++){
            for(int j=0;j<=amount;j++){
                int not_take = dp[i-1][j];
                int take = (coins[i]<=j) ? dp[i][j-coins[i]] : 0;

                dp[i][j] = (not_take + take);
            }
        }        
        return dp[n-1][amount];
    }
};
```

###### Space - optimised
```
class Solution {
public:
    int change(int amount, vector<int>& coins){
        int n = coins.size();
        vector<long long> prev(amount+1,0);

        int num_odd = 0;
        for(int i=0;i<n;i++){
            if(coins[i]%2==1)
                num_odd++;
        }

        if(amount%2==1 && num_odd==0)
            return 0;

        for(int i=0;i<=amount;i++){
            if(i%coins[0]==0)
                prev[i] = 1;
        }

        for(int i=1;i<n;i++){
            vector<long long> curr(amount+1,0);
            for(int j=0;j<=amount;j++){
                long long not_take = prev[j];
                long long take = (coins[i]<=j) ? curr[j-coins[i]] : 0;
                curr[j] = (not_take + take);
            }
            prev = curr;
        }   
        return prev[amount];
    }
};
```

Return -> [[DP on Subsequences]]
