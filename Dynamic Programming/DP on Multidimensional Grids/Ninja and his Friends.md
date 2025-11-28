https://leetcode.com/problems/cherry-pickup-ii/
###### Recursive Approach
```
class Solution {
public:
    int solve(int row,int col1,int col2,vector<vector<int>>& g,int n,int m){
        if (col1 < 0 || col1 >= m || col2 < 0 || col2 >= m)
            return 0;  

        if (row == n - 1) {
            if (col1 == col2)
                return g[row][col1];
            else
                return g[row][col1] + g[row][col2];
        }

        int ans = 0;
        for (int i = -1; i <= 1; i++) {
            for (int j = -1; j <= 1; j++) {
                int firstCol = col1 + i;
                int secCol = col2 + j;
                int cherry = g[row][col1];
                if (col1 != col2)
                    cherry += g[row][col2];
                cherry += solve(row+1,firstCol,secCol,g,n,m);
                ans = max(ans, cherry);
            }
        }
        return ans;
    }

    int cherryPickup(vector<vector<int>>& grid) {
        int n = grid.size();
        int m = grid[0].size();
        return solve(0,0,m-1,grid,n,m);
    }
};
```
###### Memoization Approach
```
class Solution {
public:
    int solve(int row,int col1,int col2,vector<vector<int>>& grid,int n,int m,vector<vector<vector<int>>> &dp){
        if (col1 < 0 || col1 >= m || col2 < 0 || col2 >= m)
            return 0;
        if(dp[row][col1][col2]!=-1)
            return dp[row][col1][col2]; 

        if (row == n - 1) {
	        dp[row][col1][col2] = grid[row][col1]
            if (col1!=col2)
                return dp[row][col1][col2]+=grid[row][col2]);
            else
                return dp[row][col1][col2];
        } 
        
        int ans = 0;
        // Trying out all combos
        for (int i = -1; i <= 1; i++) {
            for (int j = -1; j <= 1; j++) {

                int firstCol = col1 + i;
                int secCol = col2 + j;
                int cherry = grid[row][col1];

                if (col1 != col2)
                    cherry += grid[row][col2];

                cherry += solve(row+1,firstCol,secCol,grid,n,m,dp);
                ans = max(ans, cherry);
            }
        }
        return dp[row][col1][col2] = ans;
    }
    
    int cherryPickup(vector<vector<int>>& grid) {
        int n = grid.size();
        int m = grid[0].size();
        vector<vector<vector<int>>> dp(n, vector<vector<int>>(m, vector<int>(m, -1)));
        
        return solve(0,0,m-1,grid,n,m,dp);
    }
};
```

Return to  -> [[DP on 2D,3D Grids]]

