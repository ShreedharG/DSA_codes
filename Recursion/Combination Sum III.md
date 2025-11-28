https://leetcode.com/problems/combination-sum-iii/
###### My Code
```
class Solution {
public:

    void find_c(int seq_in,int id,vector<int>& seq,vector<vector<int>>& ans,vector<int>& nums,int k,int target){
        if(seq_in==k){
            if(target==0)
                ans.push_back(seq);
            return;
        }
  
        if(seq_in>k || id>=9)
            return;

        //take
        if(nums[id] <= target){
            seq.push_back(nums[index]);
            find_c(seq_in+1,id+1,seq,ans,nums,k,target-nums[index]);
            seq.pop_back();
        }

        //not take
        find_c(seq_in,id+1,seq,ans,nums,k,target);
    }

    vector<vector<int>> combinationSum3(int k, int n) {
        vector<int> sequence;
        vector<vector<int>> ans;
        vector<int> nums(9);
        for(int i=0;i<9;i++)
            nums[i]=i+1;

        find_combo(0,0,sequence,ans,nums,k,n);
        return ans;
    }
};
```
###### Cleaned Up
```
class Solution {
public:
    void find_combo(int seq_in,int index,vector<int>& sequence,vector<vector<int>>& ans,int k,int target){
        if(seq_in==k){
            if(target==0)
                ans.push_back(sequence);
            return;
        }

        for(int i=index;i<=9;i++){
            if(i>target) // No check after this
                break;
            sequence.push_back(i);
            find_combo(seq_in+1,i+1,sequence,ans,k,target-i);
            sequence.pop_back();
        }
    }

    vector<vector<int>> combinationSum3(int k, int n) {
        vector<int> sequence;
        vector<vector<int>> ans;
        find_combo(0,1,sequence,ans,k,n);
        
        return ans;        
    }
};
```

Return -> [[Recursion + Backtracking]]
