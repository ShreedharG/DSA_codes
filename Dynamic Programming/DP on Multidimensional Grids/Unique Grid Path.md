https://leetcode.com/problems/unique-paths/
###### Recursive approach
```
class Solution {
public:
    int solve(int i,int j){
        if(i==0 && j==0) return 1;
        if(i<0 || j<0) return 0;

        int up = solve(i-1,j);
        int left = solve(i,j-1);
        
        return (up+left);
    }

    int uniquePaths(int m, int n){
        return solve(m-1,n-1);        
    }
};
```
###### Memoization approach
```
class Solution {
public:
    int solve(vector<vector<int>> &dp, int i,int j){
        if(i==0 && j==0) return 1;
        if(i<0 || j<0) return 0;  

        if(dp[i][j]!=-1) return dp[i][j];  

        return (dp[i][j] = solve(dp,i-1,j) + solve(dp,i,j-1));
    }
    
    int uniquePaths(int m, int n){
        vector<vector<int>> dp(m,vector<int>(n,-1));
        return solve(dp,m-1,n-1);        
    }
};
```
###### Tabulation
```
class Solution {
public:   
    int uniquePaths(int m, int n){
        vector<vector<int>> dp(m,vector<int>(n,0));
        
        for(int i=0;i<m;i++) dp[i][0] = 1;
        for(int j=0;j<n;j++) dp[0][j] = 1;
  
        for(int i=1;i<m;i++){
            for(int j=1;j<n;j++){
                dp[i][j] = dp[i-1][j] + dp[i][j-1];
            }
        }      
        return dp[m-1][n-1];
    }
};
```

Return to  -> [[DP on 2D,3D Grids]]