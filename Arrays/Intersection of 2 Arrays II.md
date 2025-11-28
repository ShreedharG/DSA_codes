https://leetcode.com/problems/intersection-of-two-arrays-ii/?envType=problem-list-v2&envId=array

```
class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        sort(nums1.begin(), nums1.end());
        sort(nums2.begin(), nums2.end());
        vector<int> inter;
  
        int i=0, j=0;
        while(i < nums1.size() && j < nums2.size()){
            if(nums1[i] == nums2[j]){
                inter.push_back(nums1[i]);
                i++;
                j++;
            }
            else if(nums1[i] > nums2[j]) j++;
            else i++;
        }
        return inter;
    }
};
```

Return -> [[Arrays, Prefix-Suffix, Hashing, Maps]]

