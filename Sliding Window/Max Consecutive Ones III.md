https://leetcode.com/problems/max-consecutive-ones-iii/

```
class Solution {
public:
    int longestOnes(vector<int>& nums, int k) {
        int n = nums.size();
        int left = 0;
        int maxLen = 0;
        int num_zeros = 0;
  
        for(int right = 0; right < n; right++){
            if(nums[right]==0)
                num_zeros++;

            while(num_zeros > k){
                if(nums[left]==0)
                    num_zeros--;
                left++;
            }
            maxLen = max(maxLen, right-left+1);
        }
        return maxLen;
    }
};
```

Return -> [[Sliding Window, 2 Pointer Approach]]

