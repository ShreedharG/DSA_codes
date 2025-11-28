https://www.geeksforgeeks.org/problems/subset-sum-problem-1611555638/1

```
class Solution {
  public:
    bool find_sum(int index, int target, vector<int>& arr){
        if(target==0) return true;
        if(index==arr.size()) return false;
        
        //Take the element 
        if(target >= arr[index]){
            if(find_sum(index+1,target-arr[index],arr))
	            return true;
        }
        
        //Do not take
        return find_sum(index+1,target,arr);
    }
    
    bool isSubsetSum(vector<int>& arr, int sum){
        sort(arr.begin(),arr.end());
        return find_sum(0,sum,arr);
    }
};
```

Return -> [[Recursion + Backtracking]]

