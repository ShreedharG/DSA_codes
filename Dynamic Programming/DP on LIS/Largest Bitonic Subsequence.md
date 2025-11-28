https://www.geeksforgeeks.org/problems/longest-bitonic-subsequence0824/1

```
class Solution {
  public:
    int LongestBitonicSequence(int n, vector<int> &nums){
        vector<int> leftLIS(n,1);        
        for(int i=1;i<n;i++){
            for(int j=0;j<i;j++){
                if(nums[j] < nums[i])
                    leftLIS[i] = max(leftLIS[i],1+leftLIS[j]);
            }
        }

		vector<int> rightLIS(n,1);
        for(int i=n-2;i>=0;i--){
            for(int j=n-1;j>i;j--){
                if(nums[i] > nums[j])
                    rightLIS[i] = max(rightLIS[i],1+rightLIS[j]);
            }
        }
        
        int maxi = 0;
        for(int i=0;i<n;i++){
            if(rightLIS[i]>1 && leftLIS[i]>1)
                maxi = max(maxi,(rightLIS[i]+leftLIS[i]-1));
        }
        return maxi;
    }
};
```

Return -> [[DP on LIS]]