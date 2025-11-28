https://leetcode.com/problems/permutations/?source=submission-ac

```
class Solution {
public:
    void gen_permute(int index,vector<vector<int>> &ans,vector<int>& nums){
        if(index==nums.size()){
            ans.push_back(nums);
            return;
        }  
        for(int i=index;i<nums.size();i++){
            swap(nums[index],nums[i]);
            gen_permute(index+1,ans,nums);
            swap(nums[index],nums[i]);
        }
    }

    vector<vector<int>> permute(vector<int>& nums) {
        vector<vector<int>> ans; 

        gen_permute(0,ans,nums);
        return ans;
    }
};
```

Return -> [[Recursion + Backtracking]]