https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/description/

```
class Solution {
public:
    bool canMake(vector<int>& bloomDay,int days, int m, int k){
        int flowers = 0, bouquets = 0;
        for(int day:bloomDay){
            if(day <= days){
                flowers++;
                if(flowers==k){
                    bouquets++;
                    flowers = 0;
                }
            }
            else
                flowers = 0;
        }
        return (bouquets >= m);
    }

    int minDays(vector<int>& bloomDay, int m, int k) {
        long long total_req = 1LL*m*k;
        if(bloomDay.size() < total_req) return -1;  

        int low = *min_element(bloomDay.begin(),bloomDay.end());
        int high = *max_element(bloomDay.begin(),bloomDay.end());
        int ans = -1;

        while (low <= high) {
            int mid = low + (high - low)/2;

            if (canMake(bloomDay, mid, m, k)) {
                ans = mid;
                high = mid - 1;
            } 
            else
                low = mid + 1;         
        }
        return ans;
    }
};
```