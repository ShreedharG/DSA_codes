https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/

```
class Solution {
public:
    bool check_possible(vector<int>& weights,int n,int days,int limit){
        int num_days = 1;
        int lim = limit;
  
        for(int i=0;i<n;i++){
            if(weights[i] <= lim)
                lim -= weights[i];
            else{
                num_days++;
                lim = limit - weights[i];
            }   
        }
        return (num_days <= days);
    }
  
    int shipWithinDays(vector<int>& weights, int days) {
        int n = weights.size();
        int low = *max_element(weights.begin(),weights.end());
        int high = accumulate(weights.begin(),weights.end(),0);
        int ans;
  
        while(low<=high){
            int mid = low + (high-low)/2;
            if(check_possible(weights,n,days,mid)){
                ans = mid;
                high = mid-1;
            }
            else
                low = mid+1;
        }
        return ans;
    }
};
```

Return -> [[Binary search]]

