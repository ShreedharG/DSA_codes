https://leetcode.com/problems/minimum-number-of-removals-to-make-mountain-array/description/?envType=problem-list-v2&envId=greedy

```
class Solution {
public:
    int minimumMountainRemovals(vector<int>& nums) {
        int n = nums.size();
        
        vector<int> lis_lr(n,1);
        for(int i=1;i<n;i++){
            for(int j=0;j<i;j++){
                if(nums[i] > nums[j])
                    lis_lr[i] = max(lis_lr[i],1+lis_lr[j]);
            }
        }
        
        vector<int> lis_rl(n,1);
        for(int i=n-2;i>=0;i--){
            for(int j=n-1;j>i;j--){
                if(nums[i] > nums[j])
                    lis_rl[i] = max(lis_rl[i],1+lis_rl[j]);
            }
        }
        
        int max_len_mount = 0;
        for(int i=1; i < n-1; i++){
            if(lis_rl[i] > 1 && lis_lr[i] > 1)
                max_len_mount = max(max_len_mount,lis_rl[i]+lis_lr[i]-1);
        }    
        return (n-max_len_mount);
    }
};
```

Return -> [[DP on LIS]]

