https://www.geeksforgeeks.org/problems/partitions-with-given-difference/1

```
class Solution {
  public:
    int countPartitions(vector<int>& arr, int d){
        int n = arr.size();
        int total = accumulate(arr.begin(),arr.end(),0);
        
        if((total-d)%2==1 || total<d ) return 0;
        int target = (total-d)/2;
        
        vector<vector<int>> dp(n,vector<int>(target+1,0));
        
        if(arr[0]==0)
            dp[0][0] = 2;
        else{
            dp[0][0] = 1;
            if(arr[0] <= target)
                dp[0][arr[0]] = 1;
        }
        
        for(int i=1;i<n;i++){
            for(int j=0;j<=target;j++){
                if(arr[i]==0)
                    dp[i][j] = 2*dp[i-1][j];
                else{
                    dp[i][j] = (j >= arr[i]) ? dp[i-1][j-arr[i]] : 0;
                    dp[i][j] += dp[i-1][j];
	            }
            }
        }
        return dp[n-1][target];
    }
};
```

Return -> [[DP on Subsequences]]

