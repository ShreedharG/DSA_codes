https://leetcode.com/problems/summary-ranges/?envType=problem-list-v2&envId=array

```
class Solution {
public:
    vector<string> summaryRanges(vector<int>& nums) {
        int n = nums.size();
        int j = 0;
        vector<string> ans;
        for(int i = 0;i<n;i++){
            if(i+1 == n || nums[i+1] != nums[i]+1){
                if(i == j)
                    ans.push_back(to_string(nums[j]));
                else
                    ans.push_back(to_string(nums[j]) + "->" + to_string(nums[i]));

                j = i + 1;
            }    
        }
        return ans;
    }
};
```

Return -> [[Arrays, Prefix-Suffix, Hashing, Maps]]

