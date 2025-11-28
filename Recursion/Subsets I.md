https://leetcode.com/problems/subsets/

```
class Solution {
public:
    void subsequenceGen(int index,vector<vector<int>> &ans,vector<int> &arr,vector<int>& nums){
        if(index==nums.size()){
            ans.push_back(arr);
            return;
        } 

        arr.push_back(nums[index]);
        subsequenceGen(index+1,ans,arr,nums);

        arr.pop_back();
        subsequenceGen(index+1,ans,arr,nums);
    }

    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>> ans;
        vector<int> arr;  

        subsequenceGen(0,ans,arr,nums);
        return ans;        
    }
};
```

Return -> [[Recursion + Backtracking]]