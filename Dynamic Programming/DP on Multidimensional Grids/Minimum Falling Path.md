https://leetcode.com/problems/minimum-falling-path-sum/
###### Top-down Memoization
```
class Solution {
public:
    int fall(int row,int col,vector<vector<int>>& sum_m,vector<vector<int>>& matrix,int n){
        if(row==0) return (sum_m[0][col] = matrix[0][col]);
        if(sum_m[row][col]!=-1) return sum_m[row][col];  

        int rightDiag = INT_MAX,leftDiag = INT_MAX;
        int up = matrix[row][col] + fall(row-1,col,sum_m,matrix,n);
        if(col<n-1) 
	        rightDiag = matrix[row][col] + fall(row-1,col+1,sum_m,matrix,n);
        if(col>0) 
	        leftDiag = matrix[row][col] + fall(row-1,col-1,sum_m,matrix,n);

        return sum_m[row][col] = min(up,min(rightDiag, leftDiag));
    }

    int minFallingPathSum(vector<vector<int>>& matrix) {
        int n = matrix.size();
        vector<vector<int>> sum_matrix(n, vector<int>(n,-1));  

        int ans = INT_MAX;
        for(int i=0;i<n;i++){
            int sum = fall(n-1,i,sum_matrix,matrix,n);
            ans = min(ans,sum);
        } 
        return ans;
    }
};
```
###### Bottom-up Tabulation
```
class Solution {
public:
    int minFallingPathSum(vector<vector<int>>& matrix) {
        int n = matrix.size();
        vector<vector<int>> dp(n,vector<int>(n,0));

        for(int i=0;i<n;i++)
            dp[0][i] = matrix[0][i];

        for(int row=1;row<n;row++){
            for(int col=0;col<n;col++){
                int mini = dp[row-1][col];
                if(col>0) mini = min(mini,dp[row-1][col-1]);
                if(col<n-1) mini = min(mini,dp[row-1][col+1]);
                dp[row][col] = matrix[row][col] + mini;
            }
        }

        int ans = INT_MAX;
        for(int i=0;i<n;i++)
            ans = min(ans,dp[n-1][i]);

        return ans;
    }
};
```

Return -> [[DP on 2D,3D Grids]]
