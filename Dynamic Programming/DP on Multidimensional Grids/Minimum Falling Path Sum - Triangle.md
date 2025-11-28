https://leetcode.com/problems/triangle/
###### Bottom-up Tabulation
```
class Solution {
public:
    int minimumTotal(vector<vector<int>>& triangle) {
        int n = triangle.size();
        if(n==1) return triangle[0][0];
  
        vector<vector<int>> dp(n,vector<int>(n,INT_MAX));
        dp[0][0] = triangle[0][0];
        int mini = INT_MAX;

        for(int i=1;i<n;i++){
            for(int j=0;j<triangle[i].size();j++){
                int leftDiag = INT_MAX,up=INT_MAX;
                if(j<triangle[i].size()-1)
                    up = dp[i-1][j];
                if(j > 0)
                    leftDiag = dp[i-1][j-1];
                dp[i][j] = triangle[i][j] + min(up,leftDiag);
            }
        }

        for(int i=0;i<triangle[n-1].size();i++)
            mini = min(mini,dp[n-1][i]);
  
        return mini;
    }
};
```

Return to  -> [[DP on 2D,3D Grids]]


