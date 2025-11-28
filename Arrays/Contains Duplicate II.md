https://leetcode.com/problems/contains-duplicate-ii/?envType=problem-list-v2&envId=array

```
class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        unordered_set<int> s;
        int n = nums.size();
  
        for(int i=0;i<n;i++){
            if(s.count(nums[i])) return true;
  
            s.insert(nums[i]);

            if(s.size() > k) s.erase(nums[i-k]);
        }
        return false;
    }
};
```

Return -> [[Arrays, Prefix-Suffix, Hashing, Maps]]

