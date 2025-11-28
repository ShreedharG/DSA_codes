https://leetcode.com/problems/jump-game/submissions/1733435484/

```
class Solution {
public:
    bool canJump(vector<int>& nums){
        int n = nums.size();
        int max_index = 0;
        
        for(int i=0;i<n;i++){
            if(i>max_index)
                return false;
            max_index = max(max_index,nums[i]+i);
        }
        return true;
    }
};
```

Return -> [[Greedy Algorithms]]

