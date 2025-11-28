https://leetcode.com/problems/single-element-in-a-sorted-array/

```
class Solution {
public:
    int singleNonDuplicate(vector<int>& nums){
        int n = nums.size();

        if(n==1) return nums[0];
        if(nums[0]!=nums[1]) return nums[0];
        if(nums[n-1]!=nums[n-2]) return nums[n-1];  

        int low = 1;
        int high = n-2;  

        while(low<=high){
            int m = low + (high-low)/2;
            if(nums[m]!=nums[m-1] && nums[m]!=nums[m+1])
                return nums[m];
                
            if((m%2==0 && nums[m]==nums[m+1])||(m%2!=0 && nums[m]==nums[m-1]))
                low = m+1;
            else
                high = m-1;
        }
    }
};
```

Return -> [[Binary search]]