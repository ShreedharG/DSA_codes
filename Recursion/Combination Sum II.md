https://leetcode.com/problems/combination-sum-ii/

```
class Solution {
public:
    void find_sequences(vector<int>& nums,vector<vector<int>> &ans,
                        vector<int> &subset,int id,int target){
        if(target==0){
            ans.push_back(subset);
            return;
        }  

        for(int i=id; i < nums.size(); i++){
            if(i > id && nums[i]==nums[i-1])
                continue;
            if(nums[i] > target)
                break;
            subset.push_back(nums[i]);
            find_sequences(nums,ans,subset,i+1,target-nums[i]);
            subset.pop_back();            
        }
    }

    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        sort(candidates.begin(),candidates.end());
        vector<vector<int>> ans;
        vector<int> subset;  

        find_sequences(candidates,ans,subset,0,target);  
        return ans;        
    }
};
```

Return -> [[Recursion + Backtracking]]