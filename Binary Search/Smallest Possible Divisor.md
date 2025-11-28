https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/

```
class Solution {
public:
    int smallestDivisor(vector<int>& nums, int threshold) {
        int n = nums.size();
        int low = 1;
        int high = *max_element(nums.begin(),nums.end());
        int ans = low;

        while(low<=high){
            int mid = low + (high-low)/2;
            int sum = 0;
            for(int i=0;i<n;i++)
                sum += ceil((double)nums[i]/mid);

            if(sum > threshold)
                low = mid+1;
            else{
                ans = mid;
                high = mid-1;
            }
        }
        return ans;        
    }
};
```

Return -> [[Binary search]]


