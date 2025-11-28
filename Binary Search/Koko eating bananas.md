https://leetcode.com/problems/koko-eating-bananas/submissions/1653608511/

```
class Solution {
public:
    int minEatingSpeed(vector<int>& piles, int h) {
        int low = 1;
        int high = *max_element(piles.begin(),piles.end());
        int mid;
        int ans;  

        while(low<=high){
            mid = low + (high-low)/2;
            long long num_hours = 0;
            for(int i=0;i<piles.size();i++)
                num_hours+=ceil((double)piles[i]/mid);
                
            if(num_hours <= h){
                high = mid-1;
                ans = mid;
            }
            else
                low = mid+1;
        }
        return ans;
    }
};
```

Return -> [[Binary search]]