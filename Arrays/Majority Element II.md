https://leetcode.com/problems/majority-element-ii/

```
class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {
        int n = nums.size();
        if(n == 1) return {nums[0]};
        if(n == 2){
            if(nums[0]==nums[1])
                return {nums[0]};
            return nums;
        }
        vector<int> ans;
  
        int ele1 = INT_MAX, freq1 = 0;
        int ele2 = INT_MAX, freq2 = 0;
  
        for(int i=0;i<n;i++){
            if(nums[i] == ele1) freq1++;
            else if(nums[i] == ele2) freq2++;
            else if(freq1 == 0){
                freq1 = 1;
                ele1 = nums[i];
            }
            else if(freq2 == 0){
                freq2 = 1;
                ele2 = nums[i];
            }
            else{
                freq1--;
                freq2--;
            }
        }
  
        int c1 = 0, c2 = 0;
        for(auto num : nums){
            if(num == ele1) c1++;
            if(num == ele2) c2++;
        }
  
        if(c1 > n/3) ans.push_back(ele1);
        if(c2 > n/3) ans.push_back(ele2);
  
        return ans;
    }
};
```

Return -> [[Arrays, Prefix-Suffix, Hashing, Maps]]

