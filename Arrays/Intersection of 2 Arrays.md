https://leetcode.com/problems/intersection-of-two-arrays/?envType=problem-list-v2&envId=array

```
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        unordered_set<int> s(nums1.begin(), nums1.end());  
        unordered_set<int> inter;
  
        for(auto num : nums2){
            if(s.count(num))
                inter.insert(num);
        }
  
        vector<int> ans(inter.begin(), inter.end());
        return ans;
    }
};
```

Return -> [[Arrays, Prefix-Suffix, Hashing, Maps]]

