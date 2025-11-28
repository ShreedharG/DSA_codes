https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/

```
class Solution {
public:
    int findMin(vector<int>& nums) {
        int min_ele = INT_MAX;
        int low = 0;
        int high = nums.size()-1;
        int middle;

        while(low<=high){
            middle = low + (high-low)/2;
            if(nums[low]<=nums[middle]){
                min_ele = min(min_ele,nums[low]);
                low = middle+1;
            }
            else{
                min_ele = min(min_ele,nums[middle]);
                high = middle-1;
            }
        }
        return min_ele;
    }
};
```

Return -> [[Binary search]]