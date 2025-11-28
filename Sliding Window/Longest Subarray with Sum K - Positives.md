https://www.naukri.com/code360/problems/longest-subarray-with-sum-k_6682399?leftPanelTabValue=SUBMISSION

```
int longestSubarrayWithSumK(vector<int> a, long long k) {
    int n = a.size();
    int left = 0;
    int maxLen = 0;
    long long sum = 0;
  
    for(int right = 0; right < n; right++){
        sum += a[right];

        while(sum > k){
            sum -= a[left];
            left++;
        }
  
        if(sum == k)
	        maxLen = max(maxLen,right-left+1);
    }
  
    return maxLen;
}
```

Return -> [[Sliding Window, 2 Pointer Approach]]

