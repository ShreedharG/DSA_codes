https://leetcode.com/problems/combination-sum/

```
class Solution {
public:
    void find_c(int index,vector<vector<int>> &ans,vector<int> &combo,vector<int>& nums,int target){
        if(target==0){
            ans.push_back(combo);
            return;
        }

        if(index==nums.size()) return;
        //Take element
        if(nums[index] <= target){
            combo.push_back(nums[index]);
            find_c(index,ans,combo,nums,target-nums[index]);
            combo.pop_back();
        }
        //Do not take 
        find_c(index+1,ans,combo,nums,target);
    }

    vector<vector<int>> combinationSum(vector<int>& candidates, int target){
        vector<vector<int>> ans;
        vector<int> combo; 

        find_c(0,ans,combo,candidates,target);
        return ans;
    }
};
```

Return -> [[Recursion + Backtracking]]

