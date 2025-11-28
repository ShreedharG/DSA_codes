```
#include<bits/stdc++.h>
using namespace std; 

void ascSortSelection(vector<int> &arr,int n){ 
    for(int i=0;i<(n-1);i++){
        int min_index = i;
        for(int j=i+1;j<n;j++){
            if(arr[j]<arr[min_index])
                min_index = j;
        } 
        
        if(min_index==i)
            continue;
        else
            swap(arr[i],arr[min_index]);
    }
}

void descSortSelection(vector<int> &arr,int n){ 
    for(int i=0;i<(n-1);i++){
        int max_index = i;
        for(int j=i+1;j<n;j++){
            if(arr[j]>arr[max_index])
                max_index = j;
        }
        
        if(max_index==i)
            continue;
        else
            swap(arr[i],arr[max_index]);
    }
}
```

Return -> [[Sorting Algos]]
