https://www.geeksforgeeks.org/problems/perfect-sum-problem5633/1
###### Tabulation
```
class Solution {
  public:
    int perfectSum(vector<int>& arr, int target){
        int n = arr.size();
        vector<vector<int>> dp(n,vector<int>(target+1,0));
        
        if(arr[0]==0)
    		dp[0][0] = 2;
    	else{
    		dp[0][0] = 1;
    		if(arr[0] <= target)
    			dp[0][arr[0]] = 1;
    	}

    	for(int i=1;i<n;i++)
    		dp[i][0] = (arr[i]==0) ? 2*dp[i-1][0] : dp[i-1][0];
    	
    	for(int i=1;i<n;i++){
    		for(int j=0;j<=target;j++){
    			int not_take = dp[i-1][j];
    			int take = (arr[i]<=j) ? dp[i-1][j-arr[i]] : 0;
    
    			dp[i][j] = (take+not_take);
        	}
    	}
    	return dp[n-1][target];
    }
};
```

Return -> [[DP on Subsequences]]
