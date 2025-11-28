https://leetcode.com/problems/third-maximum-number/?envType=problem-list-v2&envId=array

```
class Solution {
public:
    int thirdMax(vector<int>& nums) {
        int n = nums.size();
        if(n <= 2)
            return *max_element(nums.begin(), nums.end());

        long long first = LLONG_MIN;
        long long second = LLONG_MIN;
        long long third = LLONG_MIN;
  
        for(int i=0;i<n;i++){
            if(nums[i] == first || nums[i]==second || nums[i]==third)
                continue;
  
            if(nums[i] > first){
                third = second;
                second = first;
                first = nums[i];
            }
            else if(nums[i] > second){
                third = second;
                second = nums[i];
            }
            else if(nums[i] > third)
                third = nums[i];
        }
        return (third==LLONG_MIN ? (int)first : (int)third);
    }
};
```

Return -> [[Arrays, Prefix-Suffix, Hashing, Maps]]

