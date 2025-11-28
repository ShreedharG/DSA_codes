https://leetcode.com/problems/house-robber-ii/description/

```
class Solution {
public:
    int solve(vector<int>& num) {
        int n = num.size();
        int prev2 = 0;
        int prev1 = num[0];
        int curri;   

        for(int i=1;i<n;i++){
            int take = num[i];
            if(i>1) take += prev2;

            int not_take = 0 + prev1;
            curri = max(take,not_take);
            prev2 = prev1;
            prev1 = curri;
        }
        return prev1;        
    }
    int rob(vector<int>& nums) {
        int n = nums.size();
        if(n==1) return nums[0];

        vector<int> temp1,temp2;
        for(int i=0;i<n;i++){
            if(i!=0) temp1.push_back(nums[i]);
            if(i!=n-1) temp2.push_back(nums[i]);
        }
        
        return max(solve(temp1), solve(temp2));        
    }
};
```

Return -> [[DP 1D]]