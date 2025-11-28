https://leetcode.com/problems/climbing-stairs/
###### Top-down Memoization
```
class Solution {
public:
    int solve(int n,vector<int> &dp){
		if(dp[n]!=0) return dp[n];
        if(n<=2) return dp[n] = n;       
        
        return (dp[n] = solve(n-1,dp) + solve(n-2,dp));
    }

    int climbStairs(int n) {
        vector<int> dp(n+1,0);
        return solve(n,dp);        
    }
};
```
###### Bottom-up Tabulation
```
class Solution {
public:
    int climbStairs(int n) {
        if(n<=2)
	        return n;

		vector<int> dp(n+1,0);
		dp[1] = 1;
		dp[2] = 2;
		
		for(int i=3;i<=n;i++)
			dp[i] = dp[i-1] + dp[i-2];

		 return dp[n];
    }
};
```

Return -> [[DP 1D]]