https://www.geeksforgeeks.org/problems/0-1-knapsack-problem0945/1
###### Recursive
```
class Solution {
  public:
    int max_val(int id,vector<int> &val, vector<int> &wt,int m_wt){
        if(id<0) return 0;
        
        int take = 0;
        if(wt[id]<=m_wt)
	        take = val[id]+max_val(id-1,val,wt,m_wt-wt[id]);
	        
        int not_take = max_val(id-1,val,wt,m_wt);
        
        return max(take,not_take);
    }
    int knapsack(int W, vector<int> &val, vector<int> &wt){
        int n = val.size();
        return max_val(n-1,val,wt,W);
    }
};
```
###### Top-down Memoization
```
class Solution {
  public:
    int max_val(int id,vector<int> &val,vector<int>& wt,int m_wt, vector<vector<int>>& dp){
        if(id<0) return 0;
        if(dp[id][m_wt]!=-1) return dp[id][m_wt];
        
        int take = 0;
        if(wt[id]<=m_wt)
            take = val[id]+max_val(id-1,val,wt,m_wt-wt[id],dp);
            
        int not_take = max_val(id-1,val,wt,m_wt,dp);
        
        return dp[id][m_wt] = max(take,not_take);
    }
    int knapsack(int W, vector<int> &val, vector<int> &wt){
        int n = val.size();
        vector<vector<int>> dp(n,vector<int>(W+1,-1));
        
        return max_val(n-1,val,wt,W,dp);
    }
};
```
###### Tabulation
```
class Solution {
  public:
    int knapsack(int W, vector<int> &val, vector<int> &wt){
        int n = val.size();
        vector<vector<int>> dp(n,vector<int>(W+1,0));
        
        for(int j=0;j<=W;j++){
            if(wt[0] <= j)
                dp[0][j] = val[0];
        }
            
        
        for(int i=1;i<n;i++){
            for(int j=1;j<=W;j++){
                int not_take = dp[i-1][j];
                int take = (wt[i] <= j) ? val[i]+dp[i-1][j-wt[i]] : 0; 
                
                dp[i][j] = max(take,not_take);
            }
        }
        
        return dp[n-1][W];
    }
};
```

Each cell of the DP table, `dp[i][j]`,represents the maximum value of the bag upto index `i` of the weights available and weight `j` that is total capacity.

Return -> [[DP on Subsequences]]

