https://www.geeksforgeeks.org/problems/printing-longest-increasing-subsequence/1

```
class Solution {
  public:
    vector<int> getLIS(vector<int>& arr){
        int n = arr.size();
        vector<int> dp(n,1);
        vector<int> hash_arr(n);
        for(int i=0;i<n;i++)
            hash_arr[i] = i;
            
        int maxi = 1;
        int last_id = 0;
        
        for(int i=0;i<n;i++){
            for(int j=0;j<i;j++){
                if((arr[i]>arr[j]) && (dp[i] < 1+dp[j])){
                    dp[i] = 1+dp[j];
                    hash_arr[i] = j;
                }
            }
            if(dp[i] > maxi){
                maxi = dp[i];
                last_id = i;
            }
        }
        
        vector<int> ans;
        ans.push_back(arr[last_id]);
        while(hash_arr[last_id]!=last_id){
            last_id = hash_arr[last_id];
            ans.push_back(arr[last_id]);
        }
        
        reverse(ans.begin(),ans.end());
        return ans;
    }
};
```

Return -> [[DP on LIS]]