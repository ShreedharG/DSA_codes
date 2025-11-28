https://www.geeksforgeeks.org/problems/the-painters-partition-problem1535/1

```
class Solution {
  public:
    bool check_possible(vector<int>& arr,int n,int k,int mid){
        int num_painters = 1;
        int time_taken = 0;
        
        for(int i=0;i<n;i++){
            if(time_taken+arr[i] > mid){
                num_painters++;
                time_taken = arr[i];
            }
            else
                time_taken += arr[i];
        }
        return (num_painters <= k);
    }
    
    int minTime(vector<int>& arr, int k){
        int n = arr.size();
        int low = *max_element(arr.begin(),arr.end());
        int high = accumulate(arr.begin(),arr.end(),0);
        int ans;
        
        while(low<=high){
            int mid = low + (high-low)/2;
            if(check_possible(arr,n,k,mid)){
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