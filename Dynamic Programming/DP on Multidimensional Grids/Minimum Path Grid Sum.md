https://leetcode.com/problems/minimum-path-sum/
###### Recursive Approach
```
class Solution {
public:
    int solve(vector<vector<int>>& grid,int i,int j){
        if(i==0 && j==0) return grid[0][0];
        if(i<0 || j<0) return INT_MAX;  

        int up = solve(grid,i-1,j);
        int left = solve(grid,i,j-1);  

        if(up!=INT_MAX) up+=grid[i][j];
        if(left!=INT_MAX) left+=grid[i][j];
        
        return min(up,left);
    }

    int minPathSum(vector<vector<int>>& grid){
        int m = grid.size();
        int n = grid[0].size(); 

        return solve(grid,m-1,n-1);                
    }
};
```
###### Memoization Approach
```
class Solution {
public:
    int solve(vector<vector<int>> &dp,vector<vector<int>>& grid,int i,int j){
        if(i==0 && j==0) return grid[0][0];
        if(i<0 || j<0) return INT_MAX;  

        if(dp[i][j]!=-1) return dp[i][j]; 

        int up = solve(dp,grid,i-1,j);
        int left = solve(dp,grid,i,j-1); 

        if(up!=INT_MAX) up+=grid[i][j];
        if(left!=INT_MAX) left+=grid[i][j];

        return dp[i][j] = min(up,left);
    } 

    int minPathSum(vector<vector<int>>& grid){
        int m = grid.size();
        int n = grid[0].size();
        vector<vector<int>> dp(m,vector<int>(n,-1));

        return solve(dp,grid,m-1,n-1);                
    }
};
```

Return to  -> [[DP on 2D,3D Grids]]