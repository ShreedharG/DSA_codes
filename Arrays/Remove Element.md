https://leetcode.com/problems/remove-element/?envType=problem-list-v2&envId=array

```
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int n = nums.size();
        int j = 0;
        for(int i=0;i<n;i++){
            if(nums[i] != val){
                nums[j] = nums[i];
                j++;
            }
        }
        return j;
    }
};
```

Return -> [[Arrays, Prefix-Suffix, Hashing, Maps]]

