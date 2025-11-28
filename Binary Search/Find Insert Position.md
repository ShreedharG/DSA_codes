https://leetcode.com/problems/search-insert-position/

```
class Solution {
public:
    int searchInsert(vector<int>& nums, int target){
        int low = 0;
        int high = nums.size()-1;
        int mid;  

        int floor_index = 0;
        while(low<=high){
            mid = low + (high-low)/2;
            if(nums[mid] > target)                
                high = mid-1;
            else if(nums[mid] < target){
                floor_index = mid+1;
                low = mid+1;
            }
            else
                return mid;
        }
        return floor_index;
    }
};
```

Return -> [[Binary search]]