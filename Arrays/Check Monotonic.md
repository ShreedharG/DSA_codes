https://leetcode.com/problems/monotonic-array/

```
class Solution {
public:
    bool isMonotonic(vector<int>& nums) {
        int n = nums.size();
        bool increase = true;
        for(int i=0;i<n-1;i++){
            if(nums[i] > nums[i+1]){
                increase = false;
                break;
            }
        }
  
        bool decrease = true;
        for(int i=0;i<n-1;i++){
            if(nums[i] < nums[i+1]){
                decrease = false;
                break;
            }
        }
  
        return (increase || decrease);
    }
};
```

Return -> [[Arrays, Prefix-Suffix, Hashing, Maps]]

