https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

```
class Solution {
    public:
        int maxProfit(vector<int>& prices) {        
            int max_profit = INT_MIN;
            int minPrice = INT_MAX;

            for(int i=0;i<prices.size();i++){
                minPrice = min(minPrice,prices[i]);
                max_profit = max(max_profit,prices[i]-minPrice);
            }
            return max_profit;        
        }
};
```

Return -> [[DP on Stocks]]