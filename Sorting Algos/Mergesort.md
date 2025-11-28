%% This type sorting method by recursion, first sorts the halves of an array and then merges the sorted halves via the #two-pointer approach. #divide-and-conquer%%

```
class Solution {
  public:
  
	// Merges two halves
    void merge(vector<int>& arr,int l,int middle,int r){
        vector<int> temp;
        int p1 = l;
        int p2 = middle+1;
        
        while(p1<=middle && p2<=r){
            if(arr[p1]<=arr[p2])
                temp.push_back(arr[p1++]);
            else
                temp.push_back(arr[p2++]);
        }
        
        while(p1<=middle)
            temp.push_back(arr[p1++]);
        
        while(p2<=r)
            temp.push_back(arr[p2++]);
        
        for(int i=l;i<=r;i++)
            arr[i] = temp[i-l];
    }

	// Main function that is being recursively called to divide array in two
	   equal halves
    void mergeSort(vector<int>& arr, int l, int r) {
        if(l==r)
            return;
            
        int middle = l + (r-l)/2;
        
        mergeSort(arr,l,middle);
        mergeSort(arr,middle+1,r);
        
        merge(arr,l,middle,r);
    }
};
```

Return -> [[Sorting Algos]]
