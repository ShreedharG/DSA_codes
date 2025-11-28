https://leetcode.com/problems/majority-element/

```
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int n = nums.size();
        if(n==1) return nums[0];
  
        int ele = nums[0], freq = 1;
  
        for(int i=1;i<n;i++){
            if(nums[i] == ele) freq++;
            else if(freq != 0) freq--;
            else{
                ele = nums[i];
                freq = 1;
            }
        }
        return (freq == 0) ? -1 : ele;
    }
};
```

Return -> [[Arrays, Prefix-Suffix, Hashing, Maps]]

