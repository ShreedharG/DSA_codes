https://leetcode.com/problems/subsets-ii/

```
class Solution {
public:
    void subsequenceGen(int index,vector<vector<int>> &ans,
                        vector<int> &arr,vector<int>& nums){
        ans.push_back(arr);
        for(int i=index; i<nums.size(); i++){
            if(i>index && nums[i]==nums[i-1])
                continue;
            arr.push_back(nums[i]);
            subsequenceGen(i+1,ans,arr,nums);
            arr.pop_back();                    
        }
    }  

    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        vector<vector<int>> ans;
        vector<int> arr;  

        subsequenceGen(0,ans,arr,nums);
        return ans;
    }
};
```

Return -> [[Recursion + Backtracking]]