https://www.geeksforgeeks.org/problems/nth-fibonacci-number1335/1
###### Top-down Memoization
```
class Solution {
  public:
    int solve(vector<int> &dp,int n){
        if(n<=1) return n;
        if(dp[n]!=-1) return dp[n];
        
        return (dp[n] = solve(dp,n-1) + solve(dp,n-2));
    }
    int nthFibonacci(int n) {
        vector<int> dp(n+1,-1);
        return solve(dp,n);
    }
};
```
###### Space-optimised solution
```
class Solution {
  public:
    int nthFibonacci(int n){
        if(n<=1)
            return n;
            
        int prev2 = 0;
        int prev1 = 1;
        int sum;
        
        for(int i=2;i<=n;i++){
            sum = prev1 + prev2;
            
            prev2 = prev1;
            prev1 = sum;
        }
        return sum;
    }
};
```

Return -> [[DP 1D]]