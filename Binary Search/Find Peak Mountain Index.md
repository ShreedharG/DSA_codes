https://leetcode.com/problems/peak-index-in-a-mountain-array/

```
class Solution {
public:
    int peakIndexInMountainArray(vector<int>& arr) {
        int n = arr.size();
        int low = 1;
        int high = n-2;
  
        while(low <= high){
            int mid = low + (high-low)/2;
            if(arr[mid]>arr[mid-1] && arr[mid]>arr[mid+1])
                return mid;

            if(arr[mid] > arr[mid+1])
                high = mid-1;
            else
                low = mid+1;
        }
        return low;
    }
};
```

Return -> [[Binary search]]

