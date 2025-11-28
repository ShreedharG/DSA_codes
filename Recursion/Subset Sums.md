https://www.geeksforgeeks.org/problems/subset-sums2234/1&selectedLang=python3

```
class Solution {
  public:
    void All_subsetSums(int index, int sum, vector<int> &arr, 
                    vector<int> &ans){            
        if(index==arr.size()){
            ans.push_back(sum);
            return;
        }
        
        //Take element
        All_subsetSums(index+1,sum+arr[index],arr,ans);
        
        // Do not take
        All_subsetSums(index+1,sum,arr,ans);
    }
    vector<int> subsetSums(vector<int>& arr){
        vector<int> ans;
        All_subsetSums(0,0,arr,ans);
        
        return ans;
    }
};
```

Return -> [[Recursion + Backtracking]]