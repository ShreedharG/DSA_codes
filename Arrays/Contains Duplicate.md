https://leetcode.com/problems/contains-duplicate/submissions/1799334665/?envType=problem-list-v2&envId=array

```
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        int n = nums.size();
        unordered_set<int> s;

        for(int i=0;i<n;i++){
            if(s.count(nums[i])) return true;
            s.insert(nums[i]);
        }
        return false;
    }
};
```

Return -> [[Arrays, Prefix-Suffix, Hashing, Maps]]

