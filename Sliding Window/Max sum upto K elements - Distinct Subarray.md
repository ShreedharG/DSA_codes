https://leetcode.com/problems/maximum-sum-of-distinct-subarrays-with-length-k/

```
class Solution {
public:
    long long maximumSubarraySum(vector<int>& nums, int k) {
        int n = nums.size();
        long long sum = 0;
        long long maxSum = 0;
        int left = 0;

        set<int> s;
  
        for(int right=0; right < n; right++){
            while(s.find(nums[right]) != s.end()){
                sum -= nums[left];
                s.erase(nums[left]);
                left++;
            }

            sum += nums[right];
            s.insert(nums[right]);
  
            if(right-left+1 == k){
                maxSum = max(maxSum,sum);
                sum -= nums[left];
                s.erase(nums[left]);
                left++;
            }
        }
        return maxSum;
    }
};
```

Return -> [[Sliding Window, 2 Pointer Approach]]

