https://www.geeksforgeeks.org/problems/geek-jump/1
###### Top-down Memoization table 
```
class Solution {
public:
    int solve(vector<int>& height, vector<int> &cost, int n) {
        if(cost[n] != -1) return cost[n];
        if(n == 1) return (cost[1] = 0);
        if(n == 2) return (cost[2] = abs(height[1] - height[0]));

        int oneStep = solve(height,cost,n-1) + abs(height[n-1] - height[n-2]);
        int twoStep = solve(height,cost,n-2) + abs(height[n-1] - height[n-3]);

        return (cost[n] = min(oneStep, twoStep));
    }

    int minCost(vector<int>& height) {
        int n = height.size();
        vector<int> cost(n + 1, -1);
        return solve(height, cost, n);
    }
};
```

###### Bottom-up Tabulation
```
class Solution {
public:
    int minCost(vector<int>& height) {
        int n = height.size();
        vector<int> cost(n);
        
        cost[0] = 0;
        cost[1] = abs(height[1] - height[0]);

        for(int i = 2; i < n; i++) {
            cost[i] = min(cost[i-1] + abs(height[i] - height[i-1]),
                          cost[i-2] + abs(height[i] - height[i-2]));
        }
        return (cost[n-1]);
    }
};
```

###### Space-optimised Solution
```
class Solution {
  public:
    int solve(vector<int>& height,int n){
        if(n==1) return 0;
        if(n==2) return abs(height[1]-height[0]);
        
        int prev2 = 0;
        int prev1 = abs(height[1]-height[0]);
        int curri;
        
        for(int i=2;i<n;i++){
            int oneStep = prev1 + abs(height[i]-height[i-1]);
            int twoStep = prev2 + abs(height[i]-height[i-2]);
            curri = min(oneStep,twoStep);
            
            prev2 = prev1;
            prev1 = curri;
        }
        return curri;
    }
    
    int minCost(vector<int>& height) {
        int n = height.size();
        return solve(height,n);
    }
};
```

Return -> [[DP 1D]]